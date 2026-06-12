---
title: "java jre not working in firefox"
date: 2009-05-11
forum: General Help
---

### Post by Zom-b on 2009-05-11
I have been trying to install java jre, but it doesn't work, I when in terminal and did the whole sudo install and installed the jre, the plugin for firefox and some other things restarted firefox, and it still says I dont' have java installed.

---

### Post by taurus on 2009-05-11
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by Zom-b on 2009-05-11
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

```

java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

```

---

### Post by taurus on 2009-05-11
Try install sun java 1.6 again.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  Then use the <- arrow key to answer yes to the next question.

Don't forget to restart firefox.

---

### Post by Zom-b on 2009-05-11
> **taurus said:**
> Try install sun java 1.6 again.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  Then use the <- arrow key to answer yes to the next question.

Don't forget to restart firefox.

ok when I try that it tells me this

```
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  oem-config-gtk libical0 libarts1c2a kdelibs4c2a libartsc0 bluetooth libk3b3
  obex-data-server libbtctl4 kdelibs-data kdebase-bin-kde3 libwebkit-1.0-1
  libgnokii3 liblualib50 libflac++6 libpcsclite1 k3b-data tango-icon-theme
  ubuntustudio-gdm-theme python-pyatspi libboost-signals1.34.1 libavahi-qt3-1
  python-brlapi kdebase-bin localechooser-data libdbus-qt-1-1c2
  ubuntustudio-theme oem-config gnokii-common libgnomebt0 libqt3-mt
  ubuntustudio-icon-theme liblua50 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16 libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Zom-b on 2009-05-12
any other thoughts?

---

