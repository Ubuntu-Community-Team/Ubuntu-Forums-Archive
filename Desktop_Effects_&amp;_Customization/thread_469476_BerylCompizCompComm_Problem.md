---
title: "Beryl/Compiz/CompComm Problem"
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by z0phi3l on 2007-06-09
I'm trying to install the currently available update to Beryl/Compiz and it won't install and I'm getting this error:


```
E: /var/cache/apt/archives/aquamarine_0.3.0+git20070320~3v1ubuntu2_i386.deb: trying to overwrite `/usr/lib/beryl/backends/libkconfig.la', which is also in package libberylsettings0-kconfig
E: /var/cache/apt/archives/beryl-plugins_0.3.0+git20070404~3v1ubuntu4_i386.deb: trying to overwrite `/usr/lib/beryl/libwidget.so', which is also in package beryl-widget-plugin
E: /var/cache/apt/archives/beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb: trying to overwrite `/usr/share/beryl-settings-simple/level2.Profile', which is also in package beryl-ubuntu

```


Any ideas what's going on?

---

### Post by z0phi3l on 2007-06-10
Morning bump

---

### Post by z0phi3l on 2007-06-10
Another thing I've noticed, Compiz for the first time ever works, Beryl lost it's window borders.

How do I adjust Compiz's settings?

---

### Post by z0phi3l on 2007-06-10
anyo0ne have a clue?

---

### Post by maluze on 2007-07-02
I may be able to help you out here...to help with the last problem, simply type "emerald --replace" in the terminal. If you don't have emerald theme manager, it will prompt you to download it, or do "sudo apt-get install emerald"

2) You can adjust Compiz  settings by doing Alt-F2 anywhere on the desktop, and running gconf-editor, then apps>compiz>plugins

---

