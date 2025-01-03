# ～ MSXIOI 超タイニー版 ～
![MSXIOI](/MSXIOI.jpg)  
MSXIOI(超タイニー版)は[pico9918](https://github.com/visrealm/pico9918)
の回路を可能な限り簡素化したうえでMSXカートリッジ化した物体です。
9918なので当然MSX1専用です。当方はカシオPV-7、東芝HX-21で動作を確認しました。

## ここにあるファイルについて

### MSXIOI.pdf
回路図

### MSXIOI.uf2
ビルド済のファームウェア

### pico9918-v0.4.3.patch
pico9918-v0.4.3に対するソース差分

### MSXIOI.zip
ガーバーファイル

## 御注意

### 信号電圧レベル変換回路を省略しています
RP2040のIOピンをMSXのスロット端子に直結しています。
RP2040に定格を超える電圧が加えられることになるのでRP2040は勿論、MSX本体も壊れてしまう可能性があります。
IOピンに過電流が流れる事はないと思われるので個人的には実質大丈夫ではないかと感じました。
アナログ/デジタル兼用IOピンは電流が流れてしまうのでMSXとの接続には用いていません。

### ゲームにもよりますが画面の一部領域でスプライトがちらついたり乱れたりします
本体側VDPによる垂直帰線割り込み処理と非同期に動作している事が原因です。

### 動作しない機種がある
ヤマハYIS-503IIで動作しないと思います。他にも色々あるのではないかと思います。

### MSX本体側の壊れた・欠損したVDP機能を補う事は出来ません
正常動作するMSX1で使用して下さい。

### ガーバーデータについて
[JLCPCB](https://jlcpcb.com/)向けに出力しました。

### Raspberry Pi Picoボードについて
![pico](/pico.png)  
picoボードはaliexpress等で販売されている中国製の30ピン全ピン引出しタイプのものが必要です。
写真をよく見てピン配列を確認して下さい。フラッシュメモリサイズは不問です。
秋月電子でも同様の品が販売されていますがピン配列が異なるので当方の基板では使用出来ません。

### VGAコネクタについて
何種類かあるようなので当方の基板を使用する場合はサイズをよく確認してください。

## 使い方
MSX1の何れかのスロット(基本・拡張問いません)に挿してVGA(31KHz)モニターを接続するだけす。

## トラブル

### 動作中に画面が黒くなり、起動時のように画面左下にpico9918のロゴが表示される
基本的に無い筈ですが、特定の機種、環境、シチュエーションにおいて動作中に
picoボードがリセットしてしまう事があるかもしれません。
その場合はpicoボードのRUN端子とVIN端子の間に10KΩ程度の抵抗を付けて下さい。
