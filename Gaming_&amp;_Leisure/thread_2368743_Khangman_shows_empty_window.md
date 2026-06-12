---
title: "Khangman shows empty window"
date: 2017-08-14
forum: Gaming &amp; Leisure
---

### Post by Andreyshel on 2017-08-14
Hello.
I`m trying to get khangman package working.
First some information about my system

lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

uname -a
```
Linux andriy-PC 4.4.0-91-generic #114-Ubuntu SMP Tue Aug 8 11:56:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

unity --version
```
unity 7.4.0

```


When I try to start khangman , it shows empty application form without any control elements.
For me it sounds like some required KDE-stuff is missing.
Does anybody have ideas?
Thanks in advance

---

### Post by vasa1 on 2017-08-14
> **Andreyshel said:**
> ...
For me it sounds like some required KDE-stuff is missing.
...
So how did you install the application?

---

### Post by Andreyshel on 2017-08-14
sudo apt-get install khangman
Standard Universe repository.

---

### Post by vasa1 on 2017-08-14
That should have pulled in all the dependencies!

Maybe you could post an image to show what you mean by "it shows empty applications form without any control elements"?

---

### Post by Andreyshel on 2017-08-14
khangman executed from the console shows this

khangman
```

Checking path  "/usr/share/apps/kvtml"  for kvtml files
file:///usr/share/khangman/qml/main.qml:40:5: Type MainSettingsDialog unavailable 
         MainSettingsDialog { 
         ^
file:///usr/share/khangman/qml/MainSettingsDialog.qml:25:1: module "QtQuick.Dialogs" is not installed 
     import QtQuick.Dialogs 1.2 
     ^

```

I think this [link]("https://bugzilla.redhat.com/show_bug.cgi?id=1276134") provides some useful information

> [COLOR=#000000]Maybe you could post an image to show what you mean by "it shows empty applications form without any control elements"?[/COLOR]

Image
[ATTACH=CONFIG]276393[/ATTACH]
**© 2001-2017 Anne-Marie Mahfouf**

---

### Post by vasa1 on 2017-08-14
The bug you listed mentions *qt5-qtquickcontrols* and possibly *qt5-qtmultimedia*. [s]Did you try installing those packages?[/s] But neither of those packages are present in Kubuntu 16.04! And khangman is working for me.

BTW, I couldn't open your image. You can use the paper-clip icon above the posting area text box to directly upload images to the forum.

---

### Post by vasa1 on 2017-08-14
I don't know if this list helps:```
$ apt depends khangman
khangman
  Depends: fonts-dustin
  Depends: kdeedu-kvtml-data
  Depends: libc6 (>= 2.14)
  Depends: libkeduvocdocument5abi1 (>= 4:16.04.3)
  Depends: libkf5configcore5 (>= 4.98.0)
  Depends: libkf5coreaddons5 (>= 5.6.0+git20150124.0026+15.04)
  Depends: libkf5crash5 (>= 5.15.0)
  Depends: libkf5declarative5 (>= 4.96.0)
  Depends: libkf5i18n5 (>= 4.97.0)
  Depends: libkf5newstuff5 (>= 4.95.0)
  Depends: libkf5widgetsaddons5 (>= 4.96.0)
  Depends: libkf5xmlgui5 (>= 4.96.0)
  Depends: libqt5core5a (>= 5.6.0~beta)
 |Depends: libqt5gui5 (>= 5.0.2)
  Depends: libqt5gui5-gles (>= 5.0.2)
  Depends: libqt5qml5 (>= 5.0.2)
 |Depends: libqt5quickwidgets5 (>= 5.3.0)
  Depends: libqt5quickwidgets5-gles (>= 5.3.0)
  Depends: libqt5widgets5 (>= 5.0.2)
  Depends: libqt5xml5 (>= 5.0.2)
  Depends: libstdc++6 (>= 4.1.1)
  Suggests: khelpcenter
$ 
```

---

### Post by Andreyshel on 2017-08-14
> [COLOR=#000000]The bug you listed mentions [/COLOR][I]qt5-qtquickcontrols and possibly [I]qt5-qtmultimedia. Did you try installing those packages?
[/I][/I]
It is fedora bug tracker.
Those packages do not exist in standard ubuntu repos.
Maybe there should be some equivalents, but i do not know packages names.

---

### Post by vasa1 on 2017-08-14
> **Andreyshel said:**
> It is fedora bug tracker.
Those packages do not exist in standard ubuntu repos.
Maybe there should be some equivalents, but i do not know packages names.
Please the post above in case that helps.

---

### Post by Andreyshel on 2017-08-14
apt depends khangman
```
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): fonts-dustin
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): kdeedu-kvtml-data
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libc6 (>= 2.14)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkeduvocdocument5 (>= 14.11.95)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5configcore5 (>= 4.98.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5coreaddons5 (>= 5.6.0+git20150124.0026+15.04)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5declarative5 (>= 4.96.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5i18n5 (>= 4.97.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5newstuff5 (>= 4.95.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5widgetsaddons5 (>= 4.96.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libkf5xmlgui5 (>= 4.96.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5core5a (>= 5.5.0)
 |&#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5gui5 (>= 5.0.2)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5gui5-gles (>= 5.0.2)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5qml5 (>= 5.0.2)
 |&#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5quickwidgets5 (>= 5.3.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5quickwidgets5-gles (>= 5.3.0)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5widgets5 (>= 5.0.2)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libqt5xml5 (>= 5.0.2)
  &#1047;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1110; (Depends): libstdc++6 (>= 4.1.1)
  &#1055;&#1088;&#1086;&#1087;&#1086;&#1085;&#1091;&#1108; (Suggests): khelpcenter




```
diff -w
```

4c4
<    libkeduvocdocument5abi1 (>= 4:16.04.3)
---
>   libkeduvocdocument5 (>= 14.11.95)
7d6
<    libkf5crash5 (>= 5.15.0)
13c12
<    libqt5core5a (>= 5.6.0~beta)
---
>   libqt5core5a (>= 5.5.0)



```
hmm no big difference

---

### Post by vasa1 on 2017-08-14
See if the packages mentioned in [https://github.com/webcamoid/webcamoid/issues/40#issuecomment-204985231](https://github.com/webcamoid/webcamoid/issues/40#issuecomment-204985231) are installed.

---

### Post by Andreyshel on 2017-08-15
qml-module-qtquick-dialogs missing in  dependencies.
 Thank you.

---

### Post by vasa1 on 2017-08-15
So does it work now?

---

### Post by Andreyshel on 2017-08-15
Yes

---

