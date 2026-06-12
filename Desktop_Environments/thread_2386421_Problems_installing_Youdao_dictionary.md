---
title: "Problems installing Youdao dictionary"
date: 2018-03-05
forum: Desktop Environments
---

### Post by makem2 on 2018-03-05
I have installed the deb file from:

[http://cidian.youdao.com/index-linux.html](http://cidian.youdao.com/index-linux.html)

I follow the guide:

[http://time-track.cn/install-youdaodict-in-xenial.html#comment-431](http://time-track.cn/install-youdaodict-in-xenial.html#comment-431)

Everything works out correctly and I end up with another deb file in yourdaobuild folder.

Installing this from terminal produces dependency errors. Using:

```

[FONT=arial]sudo apt-get install -f[/FONT]

```

Removes the whole install.

I appreciate that this is in Mandarin but I have been able to follow it with help and believe all is correct.

>snip
After upgrading from Ubuntu 14.04 to 16.04, Youdao can not be installed on the dictionary. Because the official deb package (Ubuntu version) relies on gstreamer0.10-plugins-ugly, the software is gone in 16.04. But in fact, the package does not affect the use of Yodao Dictionary. So we can get rid of the dependencies for the library in the deb package. Specific operations are as follows:
>snip

```

han@toshSSD:~$ dpkg -X ./youdao-dict_1.1.0-0-ubuntu_amd64.deb  youdao
./
./usr/
./usr/share/
./usr/share/icons/
./usr/share/icons/hicolor/
./usr/share/icons/hicolor/scalable/
./usr/share/icons/hicolor/scalable/apps/
./usr/share/icons/hicolor/scalable/apps/youdao-dict.svg
./usr/share/icons/hicolor/24x24/
./usr/share/icons/hicolor/24x24/apps/
./usr/share/icons/hicolor/24x24/apps/youdao-dict.png
./usr/share/icons/hicolor/96x96/
./usr/share/icons/hicolor/96x96/apps/
./usr/share/icons/hicolor/96x96/apps/youdao-dict.png
./usr/share/icons/hicolor/48x48/
./usr/share/icons/hicolor/48x48/apps/
./usr/share/icons/hicolor/48x48/apps/youdao-dict.png
./usr/share/icons/hicolor/16x16/
./usr/share/icons/hicolor/16x16/apps/
./usr/share/icons/hicolor/16x16/apps/youdao-dict.png
./usr/share/icons/hicolor/64x64/
./usr/share/icons/hicolor/64x64/apps/
./usr/share/icons/hicolor/64x64/apps/youdao-dict.png
./usr/share/youdao-dict/
./usr/share/youdao-dict/indicator-youdao.py
./usr/share/youdao-dict/dae/
./usr/share/youdao-dict/dae/qmlloader.py
./usr/share/youdao-dict/dae/process.py
./usr/share/youdao-dict/dae/assets.py
./usr/share/youdao-dict/dae/socketserver.py
./usr/share/youdao-dict/dae/filesystem.py
./usr/share/youdao-dict/dae/webview.py
./usr/share/youdao-dict/dae/trayicon.py
./usr/share/youdao-dict/dae/xutils.py
./usr/share/youdao-dict/dae/filedialog.py
./usr/share/youdao-dict/dae/socketclient.py
./usr/share/youdao-dict/dae/system.py
./usr/share/youdao-dict/dae/utils.py
./usr/share/youdao-dict/dae/window.py
./usr/share/youdao-dict/dae/codec.py
./usr/share/youdao-dict/dae/webpage.py
./usr/share/youdao-dict/dae/datajar.py
./usr/share/youdao-dict/dae/api.py
./usr/share/youdao-dict/dae/file.py
./usr/share/youdao-dict/dae/ewmh.py
./usr/share/youdao-dict/dae/events.py
./usr/share/youdao-dict/dae/shadowwindow.py
./usr/share/youdao-dict/dae/init.js
./usr/share/youdao-dict/dae/xrobot.py
./usr/share/youdao-dict/dae/__init__.py
./usr/share/youdao-dict/dae/daeclient.py
./usr/share/youdao-dict/dae/menu.py
./usr/share/youdao-dict/dae/downloader.py
./usr/share/youdao-dict/dae/plugins.py
./usr/share/youdao-dict/youdao-dict-backend.py
./usr/share/youdao-dict/res/
./usr/share/youdao-dict/res/style/
./usr/share/youdao-dict/res/style/updater.css
./usr/share/youdao-dict/res/style/global.css
./usr/share/youdao-dict/res/images/
./usr/share/youdao-dict/res/images/image-q1-2.gif
./usr/share/youdao-dict/res/images/title_back.gif
./usr/share/youdao-dict/res/images/image-q3-21.gif
./usr/share/youdao-dict/res/images/laba1.gif
./usr/share/youdao-dict/res/images/image-q3-11.gif
./usr/share/youdao-dict/res/fan.xml
./usr/share/youdao-dict/res/updater.xsl
./usr/share/youdao-dict/res/faq.html
./usr/share/youdao-dict/app/
./usr/share/youdao-dict/app/manifest.json
./usr/share/youdao-dict/app/plugins/
./usr/share/youdao-dict/app/plugins/youdao/
./usr/share/youdao-dict/app/plugins/youdao/setting_dialog.py
./usr/share/youdao-dict/app/plugins/youdao/config.py
./usr/share/youdao-dict/app/plugins/youdao/setting_dialog.ui
./usr/share/youdao-dict/app/plugins/youdao/xmltodict.py
./usr/share/youdao-dict/app/plugins/youdao/deepin_dict.so
./usr/share/youdao-dict/app/plugins/youdao/utils.py
./usr/share/youdao-dict/app/plugins/youdao/ui_setting_dialog.py
./usr/share/youdao-dict/app/plugins/youdao/window.py
./usr/share/youdao-dict/app/plugins/youdao/translate.py
./usr/share/youdao-dict/app/plugins/youdao/dbus_proxy.py
./usr/share/youdao-dict/app/plugins/youdao/api.py
./usr/share/youdao-dict/app/plugins/youdao/cssselect/
./usr/share/youdao-dict/app/plugins/youdao/cssselect/tests.py
./usr/share/youdao-dict/app/plugins/youdao/cssselect/xpath.py
./usr/share/youdao-dict/app/plugins/youdao/cssselect/parser.py
./usr/share/youdao-dict/app/plugins/youdao/cssselect/__init__.py
./usr/share/youdao-dict/app/plugins/youdao/unique.py
./usr/share/youdao-dict/app/plugins/youdao/auto_object.py
./usr/share/youdao-dict/app/plugins/youdao/tts.py
./usr/share/youdao-dict/app/plugins/youdao/qml/
./usr/share/youdao-dict/app/plugins/youdao/qml/TrayIconMenu.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico04.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico04_disable.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico08.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico02.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico05.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico06.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico09.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico01.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico03.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico10.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico07.png
./usr/share/youdao-dict/app/plugins/youdao/qml/menu_icon/menu_ico05_disable.png
./usr/share/youdao-dict/app/plugins/youdao/qml/MenuItem.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/images/
./usr/share/youdao-dict/app/plugins/youdao/qml/images/youdao-dict.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_history_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/input_shadow.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/title_bg.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/search_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_on_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/window_close_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_title_bg.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/stroke_logo.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_on_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_search_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/close_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/input_bg.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/search_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_on_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_history_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_off_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/youdao_deepin_logo.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/window_close_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_search_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/search_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/setting_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/setting_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/youdao_splash.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/sound-production-hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_history_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/mini_search_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/add_wordbook.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/dict_title_line.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_off_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/setting_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/close_press.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/close_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/sound-production-normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/clear_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/right_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/right_disable.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/left_disable.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/right_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/delete_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/delete_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/left_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/clear_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/history/left_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/pin_off_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_search_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_setting_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_close_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_copy_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_pin_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_logo_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_setting_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_logo_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_pin_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_close_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_unpin_hover.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_unpin_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_search_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/images/ocr_tools/ocr_copy_normal.png
./usr/share/youdao-dict/app/plugins/youdao/qml/TranslateContent.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/LogoWindow.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/DFlickable.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/ImageButton.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/Loading.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/OcrResultWindow.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/LinkText.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/MiniWindowMenu.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/StatusImageButton.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/ImageCheckButton.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/Constant.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/DragableArea.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/Splash.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/AboutWindow.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/StrokeResultWindow.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/MiniWindow.qml
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00009.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00008.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00001.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00003.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00011.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00006.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00004.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00005.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00002.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00010.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00007.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/loading/IMG00000.bmp
./usr/share/youdao-dict/app/plugins/youdao/qml/Player.qml
./usr/share/youdao-dict/app/plugins/youdao/pyquery/
./usr/share/youdao-dict/app/plugins/youdao/pyquery/ajax.py
./usr/share/youdao-dict/app/plugins/youdao/pyquery/cssselectpatch.py
./usr/share/youdao-dict/app/plugins/youdao/pyquery/pyquery.py
./usr/share/youdao-dict/app/plugins/youdao/pyquery/rules.py
./usr/share/youdao-dict/app/plugins/youdao/pyquery/__init__.py
./usr/share/youdao-dict/app/plugins/youdao/pyquery/openers.py
./usr/share/youdao-dict/app/plugins/youdao/__init__.py
./usr/share/youdao-dict/app/plugins/youdao/models.py
./usr/share/youdao-dict/app/plugins/youdao/youdao.db
./usr/share/youdao-dict/app/plugins/youdao/const.py
./usr/share/youdao-dict/app/assets/
./usr/share/youdao-dict/app/assets/youdao-dict.png
./usr/share/youdao-dict/app/assets/pic/
./usr/share/youdao-dict/app/assets/pic/picdict.html
./usr/share/youdao-dict/app/assets/pic/js/
./usr/share/youdao-dict/app/assets/pic/js/picdict.js
./usr/share/youdao-dict/app/assets/pic/js/jquery.js
./usr/share/youdao-dict/app/assets/pic/js/offline.js
./usr/share/youdao-dict/app/assets/pic/styles/
./usr/share/youdao-dict/app/assets/pic/styles/reset.css
./usr/share/youdao-dict/app/assets/pic/styles/icon.css
./usr/share/youdao-dict/app/assets/pic/styles/offline.css
./usr/share/youdao-dict/app/assets/pic/styles/icon/
./usr/share/youdao-dict/app/assets/pic/styles/icon/scroll-down.png
./usr/share/youdao-dict/app/assets/pic/styles/icon/offline.png
./usr/share/youdao-dict/app/assets/pic/styles/icon/scroll-up.png
./usr/share/youdao-dict/app/assets/pic/styles/icon/logo.png
./usr/share/youdao-dict/app/assets/pic/styles/icon/close.png
./usr/share/youdao-dict/app/assets/pic/styles/base.css
./usr/share/youdao-dict/app/assets/pic/styles/global_layout.css
./usr/share/youdao-dict/app/assets/pic/styles/bg.css
./usr/share/youdao-dict/app/assets/pic/offline.html
./usr/share/youdao-dict/app/assets/dist/
./usr/share/youdao-dict/app/assets/dist/business-min.js
./usr/share/youdao-dict/app/assets/index.html
./usr/share/youdao-dict/app/assets/dicts.json
./usr/share/youdao-dict/app/assets/getword.js
./usr/share/youdao-dict/app/assets/speakPk.html
./usr/share/youdao-dict/app/assets/src/
./usr/share/youdao-dict/app/assets/src/images/
./usr/share/youdao-dict/app/assets/src/images/defaultAdv.jpg
./usr/share/youdao-dict/app/assets/src/images/offline_noResult.png
./usr/share/youdao-dict/app/assets/src/images/star1.png
./usr/share/youdao-dict/app/assets/src/images/index/
./usr/share/youdao-dict/app/assets/src/images/index/wt_9415.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9975.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9669.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9929.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9602.jpg
./usr/share/youdao-dict/app/assets/src/images/index/TT.jpg
./usr/share/youdao-dict/app/assets/src/images/index/ads.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9978.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9246.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9797.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9348.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9524.jpg
./usr/share/youdao-dict/app/assets/src/images/index/20130430_daily.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9548.jpg
./usr/share/youdao-dict/app/assets/src/images/index/20130430_joke.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9935.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9936.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9772.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9930.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9767.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9974.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9677.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9529.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9754.jpg
./usr/share/youdao-dict/app/assets/src/images/index/test.png
./usr/share/youdao-dict/app/assets/src/images/index/20130430_movie.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_10082.jpg
./usr/share/youdao-dict/app/assets/src/images/index/wt_9891.jpg
./usr/share/youdao-dict/app/assets/src/images/star0.png
./usr/share/youdao-dict/app/assets/src/images/head-4.jpg
./usr/share/youdao-dict/app/assets/src/images/big-banner.gif
./usr/share/youdao-dict/app/assets/src/images/example-welcome.png
./usr/share/youdao-dict/app/assets/src/images/baike-welcome.png
./usr/share/youdao-dict/app/assets/src/styles/
./usr/share/youdao-dict/app/assets/src/styles/reset.css
./usr/share/youdao-dict/app/assets/src/styles/icon.css
./usr/share/youdao-dict/app/assets/src/styles/suggest.css
./usr/share/youdao-dict/app/assets/src/styles/dict.css
./usr/share/youdao-dict/app/assets/src/styles/spokenpk.css
./usr/share/youdao-dict/app/assets/src/styles/index.css
./usr/share/youdao-dict/app/assets/src/styles/mediaquery.css
./usr/share/youdao-dict/app/assets/src/styles/icon/
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/options-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/feedback.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/topmost-cur-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/updating.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/exit-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/topmost.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/set.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/guide-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/plugins.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/help.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/login.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/guide.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/updating-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/topmost-cur.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/logout.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/about.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/help-online-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/exit.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/help-online.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/set-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/options.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/f-size-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/help-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/cur-fz-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/topmost-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/f-size.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/plugins-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/logout-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/cur-fz.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/login-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/about-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mainMenu/feedback-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/go-index-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/headportrait_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/wordTrans.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/002.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/zan-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/argue-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/zan.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t9.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/004.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/001.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t4.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t5.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t8.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/argue.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/003.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t6.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t3.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t7.png
./usr/share/youdao-dict/app/assets/src/styles/icon/watercard/t2.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dict_star_live.png
./usr/share/youdao-dict/app/assets/src/styles/icon/tuiguang.png
./usr/share/youdao-dict/app/assets/src/styles/icon/search_short.png
./usr/share/youdao-dict/app/assets/src/styles/icon/search.png
./usr/share/youdao-dict/app/assets/src/styles/icon/headportrait.png
./usr/share/youdao-dict/app/assets/src/styles/icon/example-main-open.png
./usr/share/youdao-dict/app/assets/src/styles/icon/zan-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dict_pronounce-_icon_pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/setting.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/lang-fr.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/lang-ko.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/le-fr.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/le-ko.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/le-jap.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/langshort.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/lang-eng.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/le-eng.png
./usr/share/youdao-dict/app/assets/src/styles/icon/languageSelect/lang-jap.png
./usr/share/youdao-dict/app/assets/src/styles/icon/go_detail.png
./usr/share/youdao-dict/app/assets/src/styles/icon/devotion_clear.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mod-switch-btns.png
./usr/share/youdao-dict/app/assets/src/styles/icon/refresh.png
./usr/share/youdao-dict/app/assets/src/styles/icon/scroll-down.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/logoforvo-20.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_bad_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/icon_f_voice_pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_share_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_bad_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_xiala_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_up_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_share_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/icon_f_voice_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_up_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_xiala_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_bad_disabled.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_good_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_good_disabled.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_left_slider_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/global_voice_icon.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_right_slider_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_left_slider_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_good_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_voice/btn_right_slider_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/close_pic_dict.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dict_login.png
./usr/share/youdao-dict/app/assets/src/styles/icon/new.png
./usr/share/youdao-dict/app/assets/src/styles/icon/menu-moreop.png
./usr/share/youdao-dict/app/assets/src/styles/icon/go-index.png
./usr/share/youdao-dict/app/assets/src/styles/icon/up.png
./usr/share/youdao-dict/app/assets/src/styles/icon/nav_arrow.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/share-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/read-after-new-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/sound-production-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/read-after-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/sound-production-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/share-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/read-after-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/start_head/read-after-new-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/collapse-closed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/hasNoMic.png
./usr/share/youdao-dict/app/assets/src/styles/icon/help.png
./usr/share/youdao-dict/app/assets/src/styles/icon/feed-back.png
./usr/share/youdao-dict/app/assets/src/styles/icon/zan.png
./usr/share/youdao-dict/app/assets/src/styles/icon/close-ads-bottom.png
./usr/share/youdao-dict/app/assets/src/styles/icon/kantianxia.png
./usr/share/youdao-dict/app/assets/src/styles/icon/default.png
./usr/share/youdao-dict/app/assets/src/styles/icon/top.png
./usr/share/youdao-dict/app/assets/src/styles/icon/adPanelShadow.jpg
./usr/share/youdao-dict/app/assets/src/styles/icon/show_more.png
./usr/share/youdao-dict/app/assets/src/styles/icon/pic-for-bisheng.png
./usr/share/youdao-dict/app/assets/src/styles/icon/picyd.png
./usr/share/youdao-dict/app/assets/src/styles/icon/humanvoice.png
./usr/share/youdao-dict/app/assets/src/styles/icon/offline.png
./usr/share/youdao-dict/app/assets/src/styles/icon/example-split.png
./usr/share/youdao-dict/app/assets/src/styles/icon/infomationStream/
./usr/share/youdao-dict/app/assets/src/styles/icon/infomationStream/share.png
./usr/share/youdao-dict/app/assets/src/styles/icon/infomationStream/tip.png
./usr/share/youdao-dict/app/assets/src/styles/icon/infomationStream/1.png
./usr/share/youdao-dict/app/assets/src/styles/icon/authoritative.png
./usr/share/youdao-dict/app/assets/src/styles/icon/scroll-up.png
./usr/share/youdao-dict/app/assets/src/styles/icon/menu-moreop-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/netError.png
./usr/share/youdao-dict/app/assets/src/styles/icon/word-status.png
./usr/share/youdao-dict/app/assets/src/styles/icon/enter.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/result_top.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/most_similarity.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/spoken_pk_page.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/also_similarity.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/reload_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/beginpk.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/top-bg.jpg
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/voice_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/share.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/goback.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/voice_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/beginpk_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spokenPk/reload_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/close-head-ads.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/satisfy.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/share.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/point.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/close.png
./usr/share/youdao-dict/app/assets/src/styles/icon/everydayEnglish/page.png
./usr/share/youdao-dict/app/assets/src/styles/icon/search-input-bg.png
./usr/share/youdao-dict/app/assets/src/styles/icon/logo.png
./usr/share/youdao-dict/app/assets/src/styles/icon/handWrite.png
./usr/share/youdao-dict/app/assets/src/styles/icon/close.png
./usr/share/youdao-dict/app/assets/src/styles/icon/example-main-close.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/miniwindow-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Main-Menu-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/bbs-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-on-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Translate-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Photograph-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/youdaos-choo-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-on-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/youdaos-choo-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/youdaos-choo-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/bbs-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Main-Menu-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Main-Menu-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Translate-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/miniwindow-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Translate-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/miniwindow-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Photograph-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/bbs-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/WordsBook-on-pressed.png
./usr/share/youdao-dict/app/assets/src/styles/icon/global_menu/Photograph-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/nodata.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/joke.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/micro.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/oral-practice.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/date.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/huihui.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/other.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/card.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/article.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/connect.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/media.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/overseas.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/bilingual.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/news.png
./usr/share/youdao-dict/app/assets/src/styles/icon/info_stream/activites.png
./usr/share/youdao-dict/app/assets/src/styles/icon/devote_btn.png
./usr/share/youdao-dict/app/assets/src/styles/icon/bg/
./usr/share/youdao-dict/app/assets/src/styles/icon/bg/bg.jpg
./usr/share/youdao-dict/app/assets/src/styles/icon/top-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/gotosearch.png
./usr/share/youdao-dict/app/assets/src/styles/icon/original.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dict_pronounce-_icon_disable.png
./usr/share/youdao-dict/app/assets/src/styles/icon/tab-border.png
./usr/share/youdao-dict/app/assets/src/styles/icon/add-wordsbook.png
./usr/share/youdao-dict/app/assets/src/styles/icon/searchDown.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dict_pronounce-_icon_normal.png
./usr/share/youdao-dict/app/assets/src/styles/icon/added-wordsbook.png
./usr/share/youdao-dict/app/assets/src/styles/icon/history.png
./usr/share/youdao-dict/app/assets/src/styles/icon/dictvoice.png
./usr/share/youdao-dict/app/assets/src/styles/icon/bilingual.png
./usr/share/youdao-dict/app/assets/src/styles/icon/added-wordsbook-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/collapse.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/record-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/finish-record-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/tip.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/replay-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/spoken-read.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/replay.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/start_hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/recording.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/finish-record.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/record.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/start.png
./usr/share/youdao-dict/app/assets/src/styles/icon/spoken/waiting.gif
./usr/share/youdao-dict/app/assets/src/styles/icon/cpp_mini.png
./usr/share/youdao-dict/app/assets/src/styles/icon/load.gif
./usr/share/youdao-dict/app/assets/src/styles/icon/add-wordsbook-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/pic-to-bisheng.png
./usr/share/youdao-dict/app/assets/src/styles/icon/handWrite-hover.png
./usr/share/youdao-dict/app/assets/src/styles/icon/pagination.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/sratrSet.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/spoken.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/trans_webPage.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/trans_switch.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/diagram.png
./usr/share/youdao-dict/app/assets/src/styles/icon/guide/stroke.png
./usr/share/youdao-dict/app/assets/src/styles/icon/video-close.png
./usr/share/youdao-dict/app/assets/src/styles/icon/mini-logo.png
./usr/share/youdao-dict/app/assets/src/styles/base.css
./usr/share/youdao-dict/app/assets/src/styles/fanyi.css
./usr/share/youdao-dict/app/assets/src/styles/global_layout.css
./usr/share/youdao-dict/app/assets/src/styles/bg.css
./usr/share/youdao-dict/app/assets/src/styles/animation.css
./usr/share/youdao-dict/main.py
./usr/share/youdao-dict/backend/
./usr/share/youdao-dict/backend/tesseract/
./usr/share/youdao-dict/backend/tesseract/tesseract.py
./usr/share/youdao-dict/backend/tesseract/builders.py
./usr/share/youdao-dict/backend/tesseract/util.py
./usr/share/youdao-dict/backend/tesseract/__init__.py
./usr/share/youdao-dict/backend/event.py
./usr/share/youdao-dict/backend/utils.py
./usr/share/youdao-dict/backend/backend.py
./usr/share/youdao-dict/backend/__init__.py
./usr/share/youdao-dict/backend/gst_sound.py
./usr/share/dbus-1/
./usr/share/dbus-1/services/
./usr/share/dbus-1/services/com.youdao.backend.service
./usr/share/dbus-1/services/com.youdao.indicator.service
./usr/share/doc/
./usr/share/doc/youdao-dict/
./usr/share/doc/youdao-dict/copyright
./usr/share/doc/youdao-dict/license_ch.docx
./usr/share/doc/youdao-dict/license_ch.txt
./usr/share/doc/youdao-dict/changelog.Debian
./usr/share/applications/
./usr/share/applications/youdao-dict.desktop
./usr/bin/
./etc/
./etc/xdg/
./etc/xdg/autostart/
./etc/xdg/autostart/youdao-dict-autostart.desktop
./usr/bin/youdao-dict
han@toshSSD:~$ dpkg -e ./youdao-dict_1.1.0-0-ubuntu_amd64.deb youdao/DEBIAN
han@toshSSD:~$ dpkg-deb -b youdao youdaobuild/
dpkg-deb: building package 'youdao-dict' in 'youdaobuild//youdao-dict_1.1.0-0~ubuntu_amd64.deb'.
han@toshSSD:~$ 

```

This produces a new deb in youdaobuild but this has the same effect as the initial download. It will not install without dependency errors. According to web page replies to the post it does work so I must have gone wrong somewhere.

---

### Post by monkeybrain20122 on 2018-03-05
Actually that .deb doesn't depend on gstreamer. Here are the list of dependencies
> tesseract-ocr, tesseract-ocr-eng, tesseract-ocr-chi-sim, tesseract-ocr-chi-tra, ttf-wqy-microhei, python3, python3-pyqt5, python3-requests, python3-xlib, python3-lxml, python3-xdg, python3-pil, python3-pyqt5.qtmultimedia, python3-pyqt5.qtquick, python3-pyqt5.qtwebkit, python3-dbus, qml-module-qtquick-controls

What errors are you getting?

---

### Post by again? on 2018-03-05
monkeybrain20122 is right and the original linked deb will install and doesn't need gstreamer.
However I found when using the ubuntu deb from this [github page]("https://github.com/yomun/youdaodict_5.5"), the ubuntu indicator works where it doesn't with your linked deb.
Sound also works.
Translation of part of git hub page...
> The latest source for this Youdao dictionary is taken from Deepin 15.4.1 (youdao-dict_1.0.8-1_amd64.deb) and repackaged into a deb package that Ubuntu can use
It supports PyQt 5.6 and SIP 4.18.1 (the initial release of Ubuntu 16.10 / Fedora 24 / OpenSUSE 42.2, etc.)
[http://packages.deepin.com/deepin/pool/main/y/youdao-dict/](http://packages.deepin.com/deepin/pool/main/y/youdao-dict/)


Most of these packages you will already have but run this anyway....
```
sudo apt install python3 python3-dbus python3-requests python3-lxml python3-pil python3-xdg python3-xlib python3-pyqt5 python3-pyqt5.qtmultimedia python3-pyqt5.qtquick python3-pyqt5.qtwebkit gir1.2-appindicator3-0.1 qml-module-qtgraphicaleffects qml-module-qtquick-controls libqt5multimedia5-plugins ttf-wqy-microhei tesseract-ocr tesseract-ocr-eng tesseract-ocr-chi-sim tesseract-ocr-chi-tra
```

Download the deb file...
```
cd ~/Downloads && wget https://github.com/yomun/youdaodict_5.5/raw/master/youdao-dict_1.1.1-0~ubuntu_amd64.deb
```

Install using apt which resolves dependencies. When using apt use the full path to the deb file.
```
sudo apt install ~/Downloads/youdao-dict_1.1.1-0~ubuntu_amd64.deb
```

I don't understand chinese but all seems to be working.
Highlighting a word in any application brings up a translation pop-up with play sound option.

---

### Post by makem2 on 2018-03-06
> **monkeybrain20122 said:**
> Actually that .deb doesn't depend on gstreamer. Here are the list of dependencies


What errors are you getting?

Apart from the dependency errors, none. The program just does not appear to be installed but it is. It does not react when selected.

---

### Post by makem2 on 2018-03-06
> **guber2 said:**
> monkeybrain20122 is right and the original linked deb will install and doesn't need gstreamer.
However I found when using the ubuntu deb from this [github page]("https://github.com/yomun/youdaodict_5.5"), the ubuntu indicator works where it doesn't with your linked deb.
Sound also works.
Translation of part of git hub page...



Most of these packages you will already have but run this anyway....
```
sudo apt install python3 python3-dbus python3-requests python3-lxml python3-pil python3-xdg python3-xlib python3-pyqt5 python3-pyqt5.qtmultimedia python3-pyqt5.qtquick python3-pyqt5.qtwebkit gir1.2-appindicator3-0.1 qml-module-qtgraphicaleffects qml-module-qtquick-controls libqt5multimedia5-plugins ttf-wqy-microhei tesseract-ocr tesseract-ocr-eng tesseract-ocr-chi-sim tesseract-ocr-chi-tra
```

Download the deb file...
```
cd ~/Downloads && wget https://github.com/yomun/youdaodict_5.5/raw/master/youdao-dict_1.1.1-0~ubuntu_amd64.deb
```

Install using apt which resolves dependencies. When using apt use the full path to the deb file.
```
sudo apt install ~/Downloads/youdao-dict_1.1.1-0~ubuntu_amd64.deb
```

I don't understand chinese but all seems to be working.
Highlighting a word in any application brings up a translation pop-up with play sound option.

Yes, thank you, It does work.

I found I did need to install 245mb of those packages because they had been removed (well some of them maybe) when purging the install previously.

My wife is now a happy bunny! Thanks to you both.

---

