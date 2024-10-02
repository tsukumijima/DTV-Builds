
# DTV-Builds

TS抜き (DTV) 関連ソフトウェアのビルド済みアーカイブです。

## 概要

32bit 版・64bit 版を両方同梱しています。  
必須・よく使われるプラグインなどを一式まとめ、BonDriver 関連ファイルをセットアップするだけで利用できる状態にしてあります。

基本的に一番上の最新版をダウンロードしてください。  
過去のアーカイブは念のため残しているだけなので、利用は推奨しません。

> [!NOTE]
> 本来ビルド済みアーカイブのようなサイズの大きいバイナリは Releases に置くべきですが、歴史的経緯で今更変えられずこうなっています…。

## 注意

- **BonDriver 関連のファイルは同梱されていません。各自で準備してください。**  
- **TVTest-0.10.0-230512 / EDCB-230326 / px4_drv_winusb-241002 以降の TVTest / EDCB / px4_drv for WinUSB は、GitHub Actions によって全自動でビルドされるようになりました。**
  - 手作業由来のミスや属人化の排除により、より透明性の高いビルドに仕上がっています。  
- UI やダイヤログのフォントはすべて Meiryo UI に統一しています。
  - MS UI Gothic よりも読みやすく美しく、フォント変更によるレイアウト崩れへの影響が少ないためです。
- 前述の通り、使いやすいよう設定ファイルを変更したり、必要/よく使われるプラグインを同梱したりといくつか構成を変更している箇所があります。
  - 本家のソースコードをそのままビルドしただけのアーカイブではないことに注意してください。
  - 信頼できないようであれば自ビルドすることを推奨します。
- Visual Studio 2019 (TVTest-0.10.0-200202・EDCB-200209 より、それ以前は Visual Studio 2017) にてビルドしています。別途ランタイムが必要かもしれません。
  - ビルド毎に同梱するファイルを更新したり構成を変更したりしているため、古いバージョンには現在のバージョンでは同梱しているファイルが入っていない事があります。  
  - できるだけ新しいものを使用してください（特に TVTest-0.10.0-200202・EDCB-210216 以前の TVTest・EDCB は諸都合でおすすめしません）。
- 万全は期しているつもりですが、基本的に動くかどうかの保証はありません。利用は各自の責任にてお願いします。  

## 内容について

それぞれの Build.txt ファイルには最新のアーカイブのビルドの詳細が記載されています。使い始める前に一読しておくことをおすすめします。

### [TVTest](https://github.com/tsukumijima/TVTest)

よく使われるプラグイン一式を同梱しており、別途 BonDriver を配置すればすぐに使い始められる形で公開しています。

ビルドの詳細は [TVTest_Build.txt](https://github.com/tsukumijima/DTV-Builds/blob/master/TVTest_Build.txt) に記載しています。

### [EDCB](https://github.com/tsukumijima/EDCB)

現在主流の xtne6f 版をベースに EpgTimer 周辺の機能が改善されている tkntrec 版をビルドしています。
[EDCB Material WebUI](https://github.com/tsukumijima/EDCB_Material_WebUI) も同梱していますが、利用する場合は別途設定が必要です。

ビルドの詳細は [EDCB_Build.txt](https://github.com/tsukumijima/DTV-Builds/blob/master/EDCB_Build.txt) に記載しています。

### [px4_drv for WinUSB](https://github.com/tsukumijima/px4_drv)

[nns779/px4_drv](https://github.com/nns779/px4_drv) は2021年以降メンテナンスされていないため、新機種のドライバ追加や改善を施している [tsukumijima/px4_drv](https://github.com/tsukumijima/px4_drv) をビルドしています。

テストモードにしなくてもドライバをインストールできるよう、自己署名証明書を利用するように変更したドライバのインストールファイル (.inf) を同梱しています。  
ビルドの詳細でも記述していますが、ドライバのインストールの前に同梱の自己署名証明書をインストールする必要があります。  

また、すぐに使えるようにファームウェアを含め動作に必要なファイル一式をまとめて配置しているほか、BonDriver にエラー発生時のメッセージボックスを表示しないオプションを追加しています。

ビルドの詳細は [px4_drv_winusb_Build.txt](https://github.com/tsukumijima/DTV-Builds/blob/master/px4_drv_winusb_Build.txt) に記載しています。

### BonDriverProxyEx

スクランブル解除が可能で、さらにいくつかの機能が追加されている [HaijinW 氏のフォーク](https://github.com/HaijinW/BonDriverProxyEx) をビルドしています。  
BonDriverProxyEx の Windows サービス版と、BonDriver_Proxy も一緒に同梱しています。

ビルドの詳細は [BonDriverProxyEx_Build.txt](https://github.com/tsukumijima/DTV-Builds/blob/master/BonDriverProxyEx_Build.txt) に記載しています。  

### [TSTask](https://github.com/tsukumijima/TSTask)

RecTask 相当にするパッチを適用してスクランブル解除できるようにしたものをビルドしています。  
[TSTask-SPHD](https://github.com/tsukumijima/TSTask/tree/SPHD) は先ほどの TSTask にさらにスカパー！プレミアムサービス (SPHD) 対応にするパッチを適用したものをビルドしています。

ビルドの詳細は [TSTask_Build.txt](https://github.com/tsukumijima/DTV-Builds/blob/master/TSTask_Build.txt) に記載しています。

### FFmpeg

pthread・QSV・AMD_AMF などのライブラリ全部入りで、4.2 系以降は libaribb24 も入れてビルドしています。

Static とつく方はライブラリをそれぞれの exe にまとめたバージョン、  
Shared とつく方はライブラリを dll にまとめてファイルサイズを抑えたバージョンです。 

ファイルサイズが大きいので 32bit・64bit を分けていますが、32bit の PC でない限り 64bit の方を使うことをおすすめします。

> [!IMPORTANT]
> 2020年当時、[Zeranoe](https://nico-lab.net/zeranoe_close/) 製の Windows 版 FFmpeg ビルドには [libaribb24](https://github.com/nkoriyama/aribb24) が組み込まれていなかったため、[ffmpeg-windows-build-helpers](https://github.com/rdp/ffmpeg-windows-build-helpers) を使い独自に FFmpeg をビルドしていました。  
>
> **現在は [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds/releases) から高品質な FFmpeg ビルドが全自動で継続的に提供されています。** libaribb24 / [libaribcaption](https://github.com/xqq/libaribcaption) (より高品質な ARIB B24 デコーダー/レンダラー実装) もデフォルトで組み込まれており、私のビルドの完全上位互換です。  
> このリポジトリ内の FFmpeg ビルドは参照用に残しているもので、新規の利用は推奨しません。BtbN/FFmpeg-Builds で日々公開されている、最新の FFmpeg の利用を推奨します。

## ダウンロード

 - **TVTest**
   - TVTest-0.10.0-240717 … [TVTest-0.10.0-240717.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-240717.zip)
   - TVTest-0.10.0-240112 … [TVTest-0.10.0-240112.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-240112.zip)
   - TVTest-0.10.0-240106 … [TVTest-0.10.0-240106.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-240106.zip)
   - TVTest-0.10.0-231220 … [TVTest-0.10.0-231220.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-231220.zip)
   - TVTest-0.10.0-230927 … [TVTest-0.10.0-230927.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-230927.zip)
   - TVTest-0.10.0-230719 … [TVTest-0.10.0-230719.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-230719.zip)
   - TVTest-0.10.0-230512 … [TVTest-0.10.0-230512.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-230512.zip)
   - TVTest-0.10.0-220711 … [TVTest-0.10.0-220711.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-220711.zip)
   - TVTest-0.10.0-220323 … [TVTest-0.10.0-220323.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-220323.zip)
   - TVTest-0.10.0-210812 … [TVTest-0.10.0-210812.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-210812.zip)
   - TVTest-0.10.0-210425 … [TVTest-0.10.0-210425.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-210425.zip)
   - TVTest-0.10.0-210113 … [TVTest-0.10.0-210113.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-210113.zip)
   - TVTest-0.10.0-200913 … [TVTest-0.10.0-200913.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-200913.zip)
   - TVTest-0.10.0-200629 … [TVTest-0.10.0-200629.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-200629.zip)
   - TVTest-0.10.0-200508 … [TVTest-0.10.0-200508.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-200508.zip)
   - TVTest-0.10.0-200202 … [TVTest-0.10.0-200202.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-200202.zip)
   - TVTest-0.10.0-200103 … [TVTest-0.10.0-200103.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-200103.zip)
   - TVTest-0.10.0-191129 … [TVTest-0.10.0-191129.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-191129.zip)
   - TVTest-0.10.0-190808 … [TVTest-0.10.0-190808.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-190808.zip)
   - TVTest-0.10.0-190203 … [TVTest-0.10.0-190203.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TVTest-0.10.0-190203.zip)
 - **EDCB**
   - EDCB-240622 … [EDCB-240622.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-240622.zip)
   - EDCB-240222 … [EDCB-240222.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-240222.zip)
   - EDCB-240213 … [EDCB-240213.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-240213.zip)
   - EDCB-231229 … [EDCB-231229.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-231229.zip)
   - EDCB-231029 … [EDCB-231029.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-231029.zip)
   - EDCB-230922 … [EDCB-230922.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-230922.zip)
   - EDCB-230728 … [EDCB-230728.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-230728.zip)
   - EDCB-230326 … [EDCB-230326.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-230326.zip)
   - EDCB-220728 … [EDCB-220728.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-220728.zip)
   - EDCB-220624 … [EDCB-220624.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-220624.zip)
   - EDCB-220225 … [EDCB-220225.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-220225.zip)
   - EDCB-220122 … [EDCB-220122.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-220122.zip)
   - EDCB-211119 … [EDCB-211119.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-211119.zip)
   - EDCB-210828 … [EDCB-210828.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-210828.zip)
   - EDCB-210515 … [EDCB-210515.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-210515.zip)
   - EDCB-210216 … [EDCB-210216.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-210216.zip)
   - EDCB-201011 … [EDCB-201011.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-201011.zip)
   - EDCB-200911 … [EDCB-200911.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-200911.zip)
   - EDCB-200712 … [EDCB-200712.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-200712.zip)
   - EDCB-200419 … [EDCB-200419.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-200419.zip)
   - EDCB-200209 … [EDCB-200209.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-200209.zip)
   - EDCB-191222 … [EDCB-191222.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-191222.zip)
   - EDCB-191129 … [EDCB-191129.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-191129.zip)
   - EDCB-190814 … [EDCB-190814.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-190814.zip)
   - EDCB-190721 … [EDCB-190721.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-190721.zip)
   - EDCB-190709 … [EDCB-190709.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-190709.zip)
   - EDCB-190623 … [EDCB-190623.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/EDCB-190623.zip)
 - **px4_drv for WinUSB**
   - px4_drv_winusb-240421 … [px4_drv_winusb-240421.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/px4_drv_winusb-240421.zip)
   - px4_drv_winusb-230708 … [px4_drv_winusb-230708.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/px4_drv_winusb-230708.zip)
   - px4_drv_winusb-220215 … [px4_drv_winusb-220215.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/px4_drv_winusb-220215.zip)
   - px4_drv_winusb-220119 … [px4_drv_winusb-220119.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/px4_drv_winusb-220119.zip)
   - px4_drv_winusb-210909 … [px4_drv_winusb-210909.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/px4_drv_winusb-210909.zip)
 - **BonDriverProxyEx**
   - BonDriverProxyEx-1.1.6.6 … [BonDriverProxyEx-1.1.6.6.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/BonDriverProxyEx-1.1.6.6.zip)
 - **TSTask**
   - TSTask-0.2.0-210528 … [TSTask-0.2.0-210528.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-0.2.0-210528.zip)
   - TSTask-0.2.0-210523 … [TSTask-0.2.0-210523.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-0.2.0-210523.zip)
   - TSTask-0.2.0-200510 … [TSTask-0.2.0-200510.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-0.2.0-200510.zip)
   - TSTask-SPHD-0.2.0-210528 … [TSTask-SPHD-0.2.0-210528.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-SPHD-0.2.0-210528.zip)
   - TSTask-SPHD-0.2.0-210523 … [TSTask-SPHD-0.2.0-210523.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-SPHD-0.2.0-210523.zip)
   - TSTask-SPHD-0.2.0-200510 … [TSTask-SPHD-0.2.0-200510.zip](https://github.com/tsukumijima/DTV-Builds/raw/master/TSTask-SPHD-0.2.0-200510.zip)
 - **FFmpeg**
   - FFmpeg-4.4-32bit-Static … [FFmpeg-4.4-32bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.4-32bit-Static.7z)
   - FFmpeg-4.4-32bit-Shared … [FFmpeg-4.4-32bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.4-32bit-Shared.7z)
   - FFmpeg-4.4-64bit-Static … [FFmpeg-4.4-64bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.4-64bit-Static.7z)
   - FFmpeg-4.4-64bit-Shared … [FFmpeg-4.4-64bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.4-64bit-Shared.7z)
   - FFmpeg-4.3.1-32bit-Static … [FFmpeg-4.3.1-32bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.3.1-32bit-Static.7z)
   - FFmpeg-4.3.1-32bit-Shared … [FFmpeg-4.3.1-32bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.3.1-32bit-Shared.7z)
   - FFmpeg-4.3.1-64bit-Static … [FFmpeg-4.3.1-64bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.3.1-64bit-Static.7z)
   - FFmpeg-4.3.1-64bit-Shared … [FFmpeg-4.3.1-64bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.3.1-64bit-Shared.7z)
   - FFmpeg-4.2.4-32bit-Static … [FFmpeg-4.2.4-32bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.2.4-32bit-Static.7z)
   - FFmpeg-4.2.4-32bit-Shared … [FFmpeg-4.2.4-32bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.2.4-32bit-Shared.7z)
   - FFmpeg-4.2.4-64bit-Static … [FFmpeg-4.2.4-64bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.2.4-64bit-Static.7z)
   - FFmpeg-4.2.4-64bit-Shared … [FFmpeg-4.2.4-64bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.2.4-64bit-Shared.7z)
   - FFmpeg-4.1.6-32bit-Static … [FFmpeg-4.1.6-32bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.1.6-32bit-Static.7z)
   - FFmpeg-4.1.6-32bit-Shared … [FFmpeg-4.1.6-32bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.1.6-32bit-Shared.7z)
   - FFmpeg-4.1.6-64bit-Static … [FFmpeg-4.1.6-64bit-Static.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.1.6-64bit-Static.7z)
   - FFmpeg-4.1.6-64bit-Shared … [FFmpeg-4.1.6-64bit-Shared.7z](https://github.com/tsukumijima/DTV-Builds/raw/master/FFmpeg-4.1.6-64bit-Shared.7z)