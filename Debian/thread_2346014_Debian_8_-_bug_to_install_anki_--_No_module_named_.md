---
title: "Debian 8 - bug to install anki -- No module named QtWebKit"
date: 2016-12-10
forum: Debian
---

### Post by tylervortexbr on 2016-12-10
Hi guys!

I have a problem to run anki in Debian 8 after installed.

I follow the instructions continuous here:

[https://ubuntuforums.org/showthread.php?t=1772050&p=11125659#post11125659](https://ubuntuforums.org/showthread.php?t=1772050&p=11125659#post11125659)


And also here:

[http://askubuntu.com/a/343696/419914](http://askubuntu.com/a/343696/419914)

but I have a same error by console:


```
Traceback (most recent call last):  File "/usr/bin/anki", line 5, in <module>
    import aqt
  File "/usr/share/anki/aqt/__init__.py", line 12, in <module>
    from aqt.qt import *
  File "/usr/share/anki/aqt/qt.py", line 22, in <module>
    from PyQt4.QtWebKit import QWebPage, QWebView, QWebSettings
ImportError: No module named QtWebKit
```

My anki version is ***anki-2.0.36.deb***.


All ***QtWebKit*** packages is below:

```
$ sudo apt-file find QtWebKitkdevelop-python: /usr/share/kde4/apps/kdevpythonsupport/documentation_files/PyQt4/QtWebKit.py
kdevelop-python-data: /usr/share/kdevpythonsupport/documentation_files/PyQt4/QtWebKit.py
kdevelop-python-data: /usr/share/kdevpythonsupport/documentation_files/PyQt5/QtWebKit.py
kdevelop-python-data: /usr/share/kdevpythonsupport/documentation_files/PyQt5/QtWebKitWidgets.py
libpyside-dev: /usr/include/PySide/QtWebKit/pyside_qtwebkit_python.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebDatabase
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebElement
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebElementCollection
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebFullScreenVideoHandler
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebHapticFeedbackPlayer
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebHistory
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebHistoryInterface
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebHistoryItem
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebKitPlatformPlugin
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebNotificationData
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebNotificationPresenter
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebPluginFactory
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebSecurityOrigin
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebSelectData
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebSelectMethod
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebSettings
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebSpellChecker
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QWebTouchModifier
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QtWebKit
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QtWebKitDepends
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/QtWebKitVersion
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qtwebkitversion.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebdatabase.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebelement.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebhistory.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebhistoryinterface.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebkitglobal.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebkitplatformplugin.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebpluginfactory.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebsecurityorigin.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKit/qwebsettings.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QGraphicsWebView
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QWebFrame
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QWebHitTestResult
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QWebInspector
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QWebPage
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QWebView
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QtWebKitWidgets
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QtWebKitWidgetsDepends
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/QtWebKitWidgetsVersion
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qgraphicswebview.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qtwebkitwidgetsversion.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qwebframe.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qwebinspector.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qwebpage.h
libqt5webkit5-dev: /usr/include/x86_64-linux-gnu/qt5/QtWebKitWidgets/qwebview.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QGraphicsWebView
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebDatabase
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebElement
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebElementCollection
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebFrame
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebFullScreenVideoHandler
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebHapticFeedbackPlayer
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebHistory
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebHistoryInterface
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebHistoryItem
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebHitTestResult
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebInspector
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebKitPlatformPlugin
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebNotificationData
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebNotificationPresenter
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebPage
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebPluginFactory
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebScriptWorld
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebSecurityOrigin
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebSelectData
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebSelectMethod
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebSettings
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebSpellChecker
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebTouchModifier
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QWebView
libqtwebkit-dev: /usr/include/qt4/QtWebKit/QtWebKit
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qgraphicswebview.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebdatabase.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebelement.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebframe.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebhistory.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebhistoryinterface.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebinspector.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebkitglobal.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebkitplatformplugin.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebkitversion.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebpage.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebpluginfactory.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebscriptworld.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebsecurityorigin.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebsettings.h
libqtwebkit-dev: /usr/include/qt4/QtWebKit/qwebview.h
libqtwebkit-dev: /usr/lib/x86_64-linux-gnu/libQtWebKit.prl
libqtwebkit-dev: /usr/lib/x86_64-linux-gnu/libQtWebKit.so
libqtwebkit-dev: /usr/lib/x86_64-linux-gnu/pkgconfig/QtWebKit.pc
libqtwebkit-qmlwebkitplugin: /usr/lib/x86_64-linux-gnu/qt4/imports/QtWebKit/libqmlwebkitplugin.so
libqtwebkit-qmlwebkitplugin: /usr/lib/x86_64-linux-gnu/qt4/imports/QtWebKit/qmldir
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10.4
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/QtWebKitmod.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebdatabase.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebelement.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebhistory.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebhistoryinterface.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebkitglobal.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebpluginfactory.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebsecurityorigin.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKit/qwebsettings.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/QtWebKitWidgetsmod.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/qgraphicswebview.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/qwebframe.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/qwebinspector.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/qwebpage.sip
pyqt5-dev: /usr/share/sip/PyQt5/QtWebKitWidgets/qwebview.sip
python-enthoughtbase: /usr/lib/python2.6/dist-packages/enthought/qt/QtWebKit.py
python-enthoughtbase: /usr/lib/python2.7/dist-packages/enthought/qt/QtWebKit.py
python-enthoughtbase: /usr/share/pyshared/enthought/qt/QtWebKit.py
python-guidata: /usr/lib/python2.7/dist-packages/guidata/qt/QtWebKit.py
python-guidata: /usr/share/pyshared/guidata/qt/QtWebKit.py
python-pyface: /usr/lib/python2.7/dist-packages/pyface/qt/QtWebKit.py
python-pyqt5.qtwebkit: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKit.so
python-pyqt5.qtwebkit: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKit.x86_64-linux-gnu.so
python-pyqt5.qtwebkit: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKitWidgets.so
python-pyqt5.qtwebkit: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKitWidgets.x86_64-linux-gnu.so
python-pyqt5.qtwebkit-dbg: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKit.x86_64-linux-gnu_d.so
python-pyqt5.qtwebkit-dbg: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKitWidgets.x86_64-linux-gnu_d.so
python-pyqt5.qtwebkit-dbg: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKitWidgets_d.so
python-pyqt5.qtwebkit-dbg: /usr/lib/python2.7/dist-packages/PyQt5/QtWebKit_d.so
python-pyside.qtwebkit: /usr/lib/python2.7/dist-packages/PySide/QtWebKit.so
python-qgis: /usr/lib/python2.7/dist-packages/PyQt4/QtWebKit.x86_64-linux-gnu.so
python-qgis: /usr/lib/python2.7/dist-packages/qgis/PyQt/QtWebKit.py
python-qgis: /usr/lib/python2.7/dist-packages/qgis/PyQt/QtWebKitWidgets.py
python-qt4: /usr/lib/python2.7/dist-packages/PyQt4/QtWebKit.so
python-qt4-dbg: /usr/lib/debug/usr/lib/python2.7/dist-packages/PyQt4/QtWebKit.so
python-qt4-dbg: /usr/lib/python2.7/dist-packages/PyQt4/QtWebKit_d.so
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/QtWebKitmod.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qgraphicswebview.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebdatabase.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebelement.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebframe.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebhistory.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebhistoryinterface.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebinspector.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebkitglobal.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebkitversion.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebpage.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebpluginfactory.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebsecurityorigin.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebsettings.sip
python-qt4-dev: /usr/share/sip/PyQt4/QtWebKit/qwebview.sip
python-spyderlib: /usr/lib/python2.7/dist-packages/spyderlib/qt/QtWebKit.py
python-taurus: /usr/lib/python2.7/dist-packages/taurus/external/qt/QtWebKit.py
python-taurus: /usr/lib/python2.7/dist-packages/taurus/qt/QtWebKit.py
python3-pyqt4: /usr/lib/python3/dist-packages/PyQt4/QtWebKit.cpython-34m-x86_64-linux-gnu.so
python3-pyqt4-dbg: /usr/lib/debug/usr/lib/python3/dist-packages/PyQt4/QtWebKit.cpython-34dm-x86_64-linux-gnu.so
python3-pyqt4-dbg: /usr/lib/python3/dist-packages/PyQt4/QtWebKit.cpython-34dm-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKit.cpython-34m-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKit.cpython-35m-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKit.pyi
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKitWidgets.cpython-34m-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKitWidgets.cpython-35m-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit: /usr/lib/python3/dist-packages/PyQt5/QtWebKitWidgets.pyi
python3-pyqt5.qtwebkit-dbg: /usr/lib/python3/dist-packages/PyQt5/QtWebKit.cpython-34dm-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit-dbg: /usr/lib/python3/dist-packages/PyQt5/QtWebKit.cpython-35dm-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit-dbg: /usr/lib/python3/dist-packages/PyQt5/QtWebKitWidgets.cpython-34dm-x86_64-linux-gnu.so
python3-pyqt5.qtwebkit-dbg: /usr/lib/python3/dist-packages/PyQt5/QtWebKitWidgets.cpython-35dm-x86_64-linux-gnu.so
python3-pyside.qtwebkit: /usr/lib/python3/dist-packages/PySide/QtWebKit.cpython-34m-x86_64-linux-gnu.so
python3-pyside.qtwebkit: /usr/lib/python3/dist-packages/PySide/QtWebKit.cpython-35m-x86_64-linux-gnu.so
python3-spyderlib: /usr/lib/python3/dist-packages/spyderlib/qt/QtWebKit.py
qml-module-qtwebkit: /usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/experimental/libqmlwebkitexperimentalplugin.so
qml-module-qtwebkit: /usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/experimental/qmldir
qml-module-qtwebkit: /usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/libqmlwebkitplugin.so
qml-module-qtwebkit: /usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/plugins.qmltypes
qml-module-qtwebkit: /usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/qmldir
qtquick1-qml-plugins: /usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/libqmlwebkitplugin.so
qtquick1-qml-plugins: /usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/plugins.qmltypes
qtquick1-qml-plugins: /usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/qmldir
```

I need you help, please.
Thanks so much!

---

### Post by QLee on 2016-12-10
> **tylervortexbr said:**
> 
I have a problem to run anki in Debian 8 after installed.
...
My anki version is ***anki-2.0.36.deb***.



I have no idea where you got that package but the anki package for Debian 8 stable (Jessie) is 2.0.31+dfsg-1: all. Use a package manager to install packages from the repositories that are for your distribution. 

Have a look at this advice from the Debian Wiki:
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)

---

### Post by tylervortexbr on 2016-12-10
> **QLee said:**
> I have no idea where you got that package but the anki package for Debian 8 stable (Jessie) is 2.0.31+dfsg-1: all. Use a package manager to install packages from the repositories that are for your distribution. 

Have a look at this advice from the Debian Wiki:
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)


Hi QLee! Thanks for answer!

On own anki website for desktop version is:

 [http://ankisrs.net/#download](http://ankisrs.net/#download)


**Website note:**

```
Note: Ubuntu 16.10 and Debian unstable/testing has removing WebKit from Qt4, 
which breaks Anki and other applications. 
Until we can get Anki functioning properly on newer versions of the toolkit, 
your options are to run Anki in Wine, or obtain a copy of Qt4/WebKit from somewhere else.
```


My Debian sources list is below:

```
deb http://ftp.uk.debian.org/debian/ jessie maindeb-src http://ftp.uk.debian.org/debian/ jessie main


# jessie testing
deb http://ftp.uk.debian.org/debian/ testing main contrib non-free
deb-src http://ftp.uk.debian.org/debian testing main contrib non-free


deb http://security.debian.org/ jessie/updates main
deb-src http://security.debian.org/ jessie/updates main


# jessie-updates, previously known as 'volatile'
deb http://ftp.uk.debian.org/debian/ jessie-updates main
deb-src http://ftp.uk.debian.org/debian/ jessie-updates main
```


This source list by "testing" is for system test, it's okay?

---

### Post by tylervortexbr on 2016-12-10
Hoho! I installed this other version from python-qt4 and now anki it's run correctly. I did install **amd64.deb** version with following below:

[http://snapshot.debian.org/package/python-qt4/4.11.4%2Bdfsg-1/#python-qt4_4.11.4:2b:dfsg-1](http://snapshot.debian.org/package/python-qt4/4.11.4%2Bdfsg-1/#python-qt4_4.11.4:2b:dfsg-1)

---

### Post by tylervortexbr on 2016-12-13
This post is solved.
Thanks QLee for help me! :)

---

