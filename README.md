# Web NFC Tool

ブラウザから直接NFCタグの読み書きができるWebアプリケーションです。

## 概要

Web NFC APIを使用して、AndroidデバイスのChromeブラウザからNFCタグへのデータ書き込みと読み取りが可能です。URL、テキスト、Wi-Fi設定、Bluetooth接続情報、vCard（連絡先情報）など、さまざまなデータ形式に対応しています。

## 主な機能

### 書き込み機能

以下のデータタイプをNFCタグに書き込むことができます：

- **URL** - WebサイトのURLを書き込み
- **テキスト** - 任意のテキストデータ
- **Wi-Fi** - SSID/パスワードを含むWi-Fi接続情報（WPA/WPA2）
- **Bluetooth** - MACアドレスとデバイス名を含むBluetooth接続情報
- **vCard** - 名前、メール、電話番号、所属、URLなどの連絡先情報

### 読み取り機能

- NFCタグに保存されている全レコードをスキャンして表示
- シリアル番号、タイムスタンプ付きで履歴を保存
- WSC（Wi-Fi Simple Configuration）データの解析
- Bluetooth OOBデータの解析
- vCardデータの表示

### その他の機能

- **QRコード生成** - URLやWi-Fi接続情報のQRコードを自動生成
- **iPhone対応フォールバック** - Wi-Fi/BluetoothデータをiPhoneで利用できるようQRコードページのURLも併せて書き込み
- **データサイズ表示** - vCard書き込み時にNTAG213/215の容量に収まるかチェック

## デモ

- **メインツール**: [index.html](index.html)
- **シンプルなサンプル**: [simple-nfc-example.html](simple-nfc-example.html)

## 対応環境

### 必須要件

- **OS**: Android 7.0以降
- **ブラウザ**: Chrome 89以降
- **プロトコル**: HTTPS（またはlocalhost）

Web NFC APIは**セキュアコンテキスト**でのみ動作します。HTTPSまたはlocalhostでホストされている必要があります。

### 非対応環境

- iOS/iPhoneは読み書きに非対応（QRコード表示のみ利用可能）
- デスクトップブラウザは非対応

## 使い方

### NFCタグへの書き込み

1. WRITEタブを選択
2. データタイプ（URL、テキスト、Wi-Fi等）を選択
3. 必要な情報を入力
4. 「書き込み開始」ボタンをクリック
5. NFCタグをデバイスの背面に近づける

### NFCタグの読み取り

1. READタブを選択
2. 「スキャン開始」ボタンをクリック
3. NFCタグをデバイスの背面に近づける
4. 読み取った内容が画面に表示されます

## 技術仕様

### 対応レコード形式

- `url` - URLレコード
- `text` - テキストレコード
- `mime` - MIMEタイプレコード
  - `application/vnd.wfa.wsc` - Wi-Fi Simple Configuration
  - `application/vnd.bluetooth.ep.oob` - Bluetooth Out-of-Band
  - `text/vcard` - vCard形式

### NFCタグ容量

- **NTAG213**: 144バイト
- **NTAG215**: 504バイト
- **NTAG216**: 888バイト

vCard書き込み時、入力データのサイズをリアルタイムでチェックし、各タグの容量に収まるかを表示します。

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。

## 依存ライブラリ

- [qrcodejs](https://github.com/davidshimjs/qrcodejs) - QRコード生成用

## 参考リンク

- [Web NFC API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_NFC_API)
- [Web NFC - Chrome Developers](https://developer.chrome.com/articles/nfc/)
