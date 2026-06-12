---
title: "Major language issues"
date: 2023-10-23
forum: Desktop Environments
---

### Post by gantww on 2023-10-23
Greetings,
I use both English and Russian on my Ubuntu Studio desktop (22). I'm having a recurring issue when attempting to use the russian keyboard that makes the entire environment virtually unusable. Essentially, the system periodically just reverts to English after about ten seconds or if I change windows. When I go to languages under settings, I can see Russian in the list, but there is an icon indicating that not all pacakges are installed. However, it will not install it from there.

When I launch from the commandline (systemsettings kcm_translations), I get the following dump of stuff. I'm not sure what to do. I'm taking a Russian class and I can't even do my homework on this machine because it doesn't respect settings at all. Any ideas would be super helpful, as the current problem is forcing me to use a 10+ year old laptop that overheats and doesn't have a working battery.


file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ApplicationItem.qml:151:9: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 13. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ApplicationItem.qml:147:9: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 14. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/PageRow.qml:674:5: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 14. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/PageRow.qml:670:5: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 13. Use 'sequences: [ <key> ]' to bind to all of them.
QFSFileEngine::open: No file name specified
kf.coreaddons.desktopparser: Error: Failed to open  ""
QFileDevice::seek: IODevice is not open
QFSFileEngine::open: No file name specified
kf.coreaddons.desktopparser: Error: Failed to open  ""
QFileDevice::seek: IODevice is not open
QQmlEngine::setContextForObject(): Object already has a QQmlContext
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ApplicationItem.qml:151:9: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 13. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ApplicationItem.qml:147:9: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 14. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/PageRow.qml:674:5: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 14. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/PageRow.qml:670:5: QML Shortcut: Shortcut: Only binding to one of multiple key bindings associated with 13. Use 'sequences: [ <key> ]' to bind to all of them.
file:///usr/share/kpackage/kcms/kcm_translations/contents/ui/main.qml:132:13: QML ColumnLayout: Cannot anchor to an item that isn't a parent or sibling.
qml: The item SubCategoryPage_QMLTYPE_114(0x555a22096e50) is already in the PageRow
org.kde.kcm_translations: Not all missing packages managed to resolve! ("gimp-help-ru", "hunspell-ru", "hyphen-ru", "language-pack-gnome-ru", "language-pack-ru", "libreoffice-help-ru", "libreoffice-l10n-ru", "mythes-ru", "thunderbird-locale-ru") ("gimp-help-ru;2.10.0-1;all;ubuntu-jammy-universe", "hunspell-ru;1:7.2.0-2;all;ubuntu-jammy-main", "hyphen-ru;20030310-1ubuntu3;all;ubuntu-jammy-main", "language-pack-gnome-ru;1:22.04+20230801;all;ubuntu-jammy-updates-main", "language-pack-gnome-ru;1:22.04+20220415;all;ubuntu-jammy-main", "language-pack-ru;1:22.04+20230801;all;ubuntu-jammy-updates-main", "language-pack-ru;1:22.04+20220415;all;ubuntu-jammy-main", "libreoffice-help-ru;1:7.3.7-0ubuntu0.22.04.3;all;ubuntu-jammy-updates-main", "libreoffice-help-ru;1:7.3.2-0ubuntu2;all;ubuntu-jammy-main", "libreoffice-l10n-ru;1:7.3.7-0ubuntu0.22.04.3;all;ubuntu-jammy-updates-main", "libreoffice-l10n-ru;1:7.3.2-0ubuntu2;all;ubuntu-jammy-main", "mythes-ru;1:7.2.0-2;all;ubuntu-jammy-main", "thunderbird-locale-ru;1:115.3.1+build1-0ubuntu0.22.04.2;amd64;ubuntu-jammy-updates-main", "thunderbird-locale-ru;1:91.8.0+build2-0ubuntu1;amd64;ubuntu-jammy-main")

---

### Post by gantww on 2023-10-23
I tried using the get language support tool. That definitely installed some stuff. However, the system is still persisting in changing input method when I change apps. Is there some setting somewhere that tells it the input method is per app?

Edit: It's even worse than that. I can set it to Russian in chrome on this textbox and it will stay put. But as soon as I click out, it's back to english.

---

