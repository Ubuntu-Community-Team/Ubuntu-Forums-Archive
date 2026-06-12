---
title: "Help compiling"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by Opeth115 on 2007-05-28
Well im trying to compile the domino theme but every time i try i get the same error

```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
```

anything i could do to fix this?

---

### Post by tatewaki on 2007-05-28
You just need to install the xlibs-dev package

just run: "sudo aptitude install xlibs-dev" from a console

---

### Post by Ateo on 2007-05-28
> **tatewaki said:**
> You just need to install the xlibs-dev package

Not correct.

The correct packages needed are: xorg-dev && xserver-xorg-dev

Those will pull in all xorg related development libraries needed for compiling apps for Xorg.

---

### Post by tatewaki on 2007-06-04
that was the packet i needed when I got the error, but i stand corrected :) Hmm i always wondered why people was talking about dependenci hell, and now i know

---

### Post by Opeth115 on 2007-07-06
Ok trhat solved that but now i get this...

```
dominoclient.h:13:31: error: kcommondecoration.h: No such file or directory
dominoclient.h:14:32: error: kdecorationfactory.h: No such file or directory
dominoclient.h:23: error: expected class-name before '{' token
dominoclient.h:27: error: ISO C++ forbids declaration of 'KDecoration' with no type
dominoclient.h:27: error: expected ';' before '*' token
dominoclient.h:29: error: 'Ability' has not been declared
dominoclient.h:52: error: expected class-name before '{' token
dominoclient.h:54: error: expected `)' before 'type'
dominoclient.h:71: error: expected class-name before '{' token
dominoclient.h:74: error: expected `)' before '*' token
dominoclient.h:80: error: 'DecorationBehaviour' has not been declared
dominoclient.h:81: error: 'LayoutMetric' has not been declared
dominoclient.h:81: error: expected ',' or '...' before '*' token
dominoclient.h:81: error: ISO C++ forbids declaration of 'KCommonDecorationButton' with no type
dominoclient.h:82: error: ISO C++ forbids declaration of 'KCommonDecorationButton' with no type
dominoclient.h:82: error: 'KCommonDecorationButton' declared as a 'virtual' field
dominoclient.h:82: error: expected ';' before '*' token
dominoclient.h:105: error: ISO C++ forbids declaration of 'QButton' with no type
dominoclient.h:105: error: expected ';' before '*' token
dominoclient.h:81: error: default argument missing for parameter 3 of 'virtual int Domino::DominoClient::layoutMetric(int, bool, int) const'
dominoclient.cpp:119: error: expected constructor, destructor, or type conversion before '*' token
dominoclient.cpp: In member function 'bool Domino::DominoHandler::reset(long unsigned int)':
dominoclient.cpp:128: error: 'SettingColors' was not declared in this scope
dominoclient.cpp:135: error: 'SettingDecoration' was not declared in this scope
dominoclient.cpp:135: error: 'SettingFont' was not declared in this scope
dominoclient.cpp:135: error: 'SettingBorder' was not declared in this scope
dominoclient.cpp:138: error: 'resetDecorations' was not declared in this scope
dominoclient.cpp: In member function 'long unsigned int Domino::DominoHandler::readConfig(bool)':
dominoclient.cpp:149: error: 'options' was not declared in this scope
dominoclient.cpp:177: error: 'SettingColors' was not declared in this scope
dominoclient.cpp: At global scope:
dominoclient.cpp:491: error: 'bool Domino::DominoHandler::supports' is not a static member of 'class Domino::DominoHandler'
dominoclient.cpp:491: error: 'Ability' was not declared in this scope
dominoclient.cpp:492: error: expected ',' or ';' before '{' token
dominoclient.cpp:514: error: expected `)' before 'type'
dominoclient.cpp: In member function 'void Domino::DominoButton::reset(long unsigned int)':
dominoclient.cpp:540: error: 'SizeChange' was not declared in this scope
dominoclient.cpp:540: error: 'ManualReset' was not declared in this scope
dominoclient.cpp:541: error: 'setBackgroundOrigin' was not declared in this scope
dominoclient.cpp:542: error: 'setErasePixmap' was not declared in this scope
dominoclient.cpp:546: error: 'DecorationReset' was not declared in this scope
dominoclient.cpp:546: error: 'ManualReset' was not declared in this scope
dominoclient.cpp:546: error: 'SizeChange' was not declared in this scope
dominoclient.cpp:546: error: 'StateChange' was not declared in this scope
dominoclient.cpp:547: error: 'class Domino::DominoButton' has no member named 'update'
dominoclient.cpp: In member function 'void Domino::DominoButton::drawButton(QPainter*)':
dominoclient.cpp:559: error: 'isDown' was not declared in this scope
dominoclient.cpp:559: error: 'isOn' was not declared in this scope
dominoclient.cpp:560: error: 'decoration' was not declared in this scope
dominoclient.cpp:561: error: 'type' was not declared in this scope
dominoclient.cpp:562: error: 'CloseButton' was not declared in this scope
dominoclient.cpp:565: error: 'HelpButton' was not declared in this scope
dominoclient.cpp:568: error: 'MinButton' was not declared in this scope
dominoclient.cpp:571: error: 'MaxButton' was not declared in this scope
dominoclient.cpp:574: error: 'OnAllDesktopsButton' was not declared in this scope
dominoclient.cpp:577: error: 'ShadeButton' was not declared in this scope
dominoclient.cpp:580: error: 'AboveButton' was not declared in this scope
dominoclient.cpp:583: error: 'BelowButton' was not declared in this scope
dominoclient.cpp:586: error: 'MenuButton' was not declared in this scope
dominoclient.cpp:592: error: 'type' was not declared in this scope
dominoclient.cpp:592: error: 'MenuButton' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoButton::enterEvent(QEvent*)':
dominoclient.cpp:603: error: 'class Domino::DominoClient' has no member named 'isActive'
dominoclient.cpp:607: error: 'repaint' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoButton::leaveEvent(QEvent*)':
dominoclient.cpp:614: error: 'repaint' was not declared in this scope
dominoclient.cpp: At global scope:
dominoclient.cpp:621: error: expected `)' before '*' token
dominoclient.cpp:654: error: 'bool Domino::DominoClient::decorationBehaviour' is not a static member of 'class Domino::DominoClient'
dominoclient.cpp:654: error: 'DecorationBehaviour' was not declared in this scope
dominoclient.cpp:654: error: expected ',' or ';' before 'const'
dominoclient.cpp:668: error: 'int Domino::DominoClient::layoutMetric' is not a static member of 'class Domino::DominoClient'
dominoclient.cpp:668: error: 'LayoutMetric' was not declared in this scope
dominoclient.cpp:668: error: expected primary-expression before 'bool'
dominoclient.cpp:668: error: expected primary-expression before 'const'
dominoclient.cpp:668: error: initializer expression list treated as compound expression
dominoclient.cpp:668: error: expected ',' or ';' before 'const'
dominoclient.cpp:720: error: expected constructor, destructor, or type conversion before '*' token
dominoclient.cpp: In member function 'void Domino::DominoClient::init()':
dominoclient.cpp:763: error: 'menuButton' was not declared in this scope
dominoclient.cpp:766: error: 'KDecoration' has not been declared
dominoclient.cpp:766: error: 'WNoAutoErase' was not declared in this scope
dominoclient.cpp:766: error: 'WStaticContents' was not declared in this scope
dominoclient.cpp:767: error: 'setMainWidget' was not declared in this scope
dominoclient.cpp:769: error: 'widget' was not declared in this scope
dominoclient.cpp:769: error: 'NoBackground' was not declared in this scope
dominoclient.cpp:773: error: 'KCommonDecoration' has not been declared
dominoclient.cpp:773: error: 'SettingButtons' was not declared in this scope
dominoclient.cpp:775: error: 'connect' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::createLayout()':
dominoclient.cpp:784: error: 'widget' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::reset(long unsigned int)':
dominoclient.cpp:858: error: 'widget' was not declared in this scope
dominoclient.cpp:859: error: 'KCommonDecoration' has not been declared
dominoclient.cpp:860: error: 'KCommonDecoration' has not been declared
dominoclient.cpp: In member function 'void Domino::DominoClient::updateMask()':
dominoclient.cpp:869: error: 'maximizeMode' was not declared in this scope
dominoclient.cpp:869: error: 'MaximizeFull' was not declared in this scope
dominoclient.cpp:869: error: 'options' was not declared in this scope
dominoclient.cpp:870: error: 'clearMask' was not declared in this scope
dominoclient.cpp:873: error: 'widget' was not declared in this scope
dominoclient.cpp:880: error: 'setMask' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::updateCaption()':
dominoclient.cpp:892: error: 'buttonsLeftWidth' was not declared in this scope
dominoclient.cpp:893: error: 'buttonsRightWidth' was not declared in this scope
dominoclient.cpp:895: error: 'options' was not declared in this scope
dominoclient.cpp:897: error: 'caption' was not declared in this scope
dominoclient.cpp:903: error: 'KDecorationDefines' has not been declared
dominoclient.cpp:903: error: 'isActive' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::activeChange()':
dominoclient.cpp:914: error: 'updateButtons' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::iconChange()':
dominoclient.cpp:920: error: 'menuButton' was not declared in this scope
dominoclient.cpp:922: error: 'KDecoration' has not been declared
dominoclient.cpp:922: error: incomplete type 'QIconSet' used in nested name specifier
dominoclient.cpp:922: error: incomplete type 'QIconSet' used in nested name specifier
dominoclient.cpp: In member function 'void Domino::DominoClient::menuButtonDestroyed()':
dominoclient.cpp:932: error: 'menuButton' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::slotShade()':
dominoclient.cpp:937: error: 'isSetShade' was not declared in this scope
dominoclient.cpp:937: error: 'setShade' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::borders(int&, int&, int&, int&) const':
dominoclient.cpp:944: error: 'LM_BorderLeft' was not declared in this scope
dominoclient.cpp:945: error: 'LM_BorderRight' was not declared in this scope
dominoclient.cpp:946: error: 'LM_BorderBottom' was not declared in this scope
dominoclient.cpp:947: error: 'LM_TitleHeight' was not declared in this scope
dominoclient.cpp:948: error: 'LM_TitleEdgeTop' was not declared in this scope
dominoclient.cpp:949: error: 'LM_TitleEdgeBottom' was not declared in this scope
dominoclient.cpp:951: error: 'widget' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::shadeChange()':
dominoclient.cpp:957: error: 'isSetShade' was not declared in this scope
dominoclient.cpp:968: error: 'widget' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::resize(const QSize&)':
dominoclient.cpp:974: error: 'widget' was not declared in this scope
dominoclient.cpp:975: error: 'maximizeMode' was not declared in this scope
dominoclient.cpp:975: error: 'MaximizeFull' was not declared in this scope
dominoclient.cpp:975: error: 'options' was not declared in this scope
dominoclient.cpp: In member function 'void Domino::DominoClient::resizeEvent(QResizeEvent*)':
dominoclient.cpp:999: error: 'KCommonDecoration' has not been declared
dominoclient.cpp: In member function 'bool Domino::DominoClient::eventFilter(QObject*, QEvent*)':
dominoclient.cpp:1028: error: 'mouseDoubleClickEvent' was not declared in this scope
dominoclient.cpp:1031: error: 'isSetShade' was not declared in this scope
dominoclient.cpp:1032: error: 'wheelEvent' was not declared in this scope
dominoclient.cpp:1035: error: 'processMousePressEvent' was not declared in this scope
dominoclient.cpp:1040: error: 'updateButtons' was not declared in this scope
dominoclient.cpp: In member function 'virtual void Domino::TitleBar::enterEvent(QEvent*)':
dominoclient.cpp:1060: error: 'class Domino::DominoClient' has no member named 'isActive'
dominoclient.cpp:1066: error: 'class Domino::DominoClient' has no member named 'updateButtons'
dominoclient.cpp: In member function 'virtual bool Domino::TitleBar::eventFilter(QObject*, QEvent*)':
dominoclient.cpp:1074: error: 'class Domino::DominoClient' has no member named 'isActive'
dominoclient.cpp:1076: error: expected type-specifier before 'QButton'
dominoclient.cpp:1076: error: expected `>' before 'QButton'
dominoclient.cpp:1076: error: expected `(' before 'QButton'
dominoclient.cpp:1076: error: 'QButton' was not declared in this scope
dominoclient.cpp:1076: error: expected primary-expression before '>' token
dominoclient.cpp:1076: error: expected `)' before '{' token
dominoclient.cpp:1083: error: expected primary-expression before '}' token
dominoclient.cpp:1083: error: expected `;' before '}' token
dominoclient.cpp: At global scope:
dominoclient.cpp:1176: error: expected constructor, destructor, or type conversion before '*' token
dominoclient.moc: In static member function 'static QMetaObject* Domino::DominoClient::staticMetaObject()':
dominoclient.moc:54: error: 'KCommonDecoration' has not been declared
dominoclient.moc: In member function 'virtual void* Domino::DominoClient::qt_cast(const char*)':
dominoclient.moc:78: error: 'KCommonDecoration' has not been declared
dominoclient.moc: In member function 'virtual bool Domino::DominoClient::qt_invoke(int, QUObject*)':
dominoclient.moc:87: error: 'KCommonDecoration' has not been declared
dominoclient.moc: In member function 'virtual bool Domino::DominoClient::qt_emit(int, QUObject*)':
dominoclient.moc:94: error: 'KCommonDecoration' has not been declared
dominoclient.moc: In member function 'virtual bool Domino::DominoClient::qt_property(int, int, QVariant*)':
dominoclient.moc:100: error: 'KCommonDecoration' has not been declared
make[3]: *** [dominoclient.lo] Error 1
make[3]: Leaving directory `/home/matt/domino-0.4/client'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matt/domino-0.4/client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/domino-0.4'
make: *** [all] Error 2

```

---

### Post by Opeth115 on 2007-07-08
anyone? yes no?

---

