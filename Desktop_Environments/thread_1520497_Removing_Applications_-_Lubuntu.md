---
title: "Removing Applications - Lubuntu"
date: 2010-06-29
forum: Desktop Environments
---

### Post by owain123 on 2010-06-29
Trying to remove some applications installed on Lubuntu like Chromium and Abiword. When I try remove them it tries to remove Lubuntu-Desktop.
Is there a way I can stop it from doing this?

---

### Post by ajgreeny on 2010-06-29
Not really.  The lubuntu-desktop is just a meta-package and not important unless you are doing a distro upgrade from version to version.

You could try installing synaptic, though it may require a lot of gtk library packages, but if you had that you could try in the GUI setting the system not to include recommended packages as dependencies, though I am not sure if that affects removals as well as installations of packages.  You can also do installations that way with apt-get.  See ```
man apt-get
``` for all the details.

---

### Post by XSAlliN on 2010-06-29
Chromium is being forced with Lubuntu?! :confused: Than that's a sad project. Thanx for info, considering this - I'll never recommend it to anyone... To bad, LXDE being a good alternative for those that want to switch from Windows to Linux... guess that lives Kubuntu or maybe XFCE.

---

### Post by cavalier911 on 2010-06-30
Removing chromium does not break lubuntu.
I install Opera 10.11 then use aptitude to remove lubuntu-desktop, chromium-browser,chromium-codecs-ffmpeg,chromium-browser inspector,chromium-browser-l10n. 
No problems,nothings broken,everything works.
See: [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp) How-to/Beginners/Removing a program and lubuntu-desktop :guitar:

---

