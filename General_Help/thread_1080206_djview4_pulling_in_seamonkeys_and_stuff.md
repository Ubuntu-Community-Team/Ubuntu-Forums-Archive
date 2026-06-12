---
title: "djview4 pulling in seamonkeys and stuff"
date: 2009-02-25
forum: General Help
---

### Post by mathfeel on 2009-02-25
I needed a djvu viewer and so I tried to apt-get djview4:

```
$ sudo apt-get install -s djview4
[sudo] password for mzhang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static linux-restricted-modules-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  djvulibre-desktop djvulibre-plugin seamonkey-browser
  seamonkey-gnome-support
Suggested packages:
  djvulibre-bin seamonkey-mailnews seamonkey-dom-inspector
Recommended packages:
  mozilla-browser mozilla mozilla-firefox iceweasel iceape-browser
  konqueror galeon netscape-base-4 netscape
The following packages will be REMOVED:
  libdjvulibre15
The following NEW packages will be installed:
  djview4 djvulibre-desktop djvulibre-plugin seamonkey-browser
  seamonkey-gnome-support
0 upgraded, 5 newly installed, 1 to remove and 1 not upgraded.
Remv libdjvulibre15 [3.5.20-2]
Inst djview4 (4.3-5 Ubuntu:8.10/intrepid)
Inst djvulibre-desktop (3.5.20-7ubuntu3 Ubuntu:8.10/intrepid)
Inst djvulibre-plugin (3.5.20-7ubuntu3 Ubuntu:8.10/intrepid)
Inst seamonkey-browser (1.1.12+nobinonly-0ubuntu1 Ubuntu:8.10/intrepid)
Inst seamonkey-gnome-support (1.1.12+nobinonly-0ubuntu1 Ubuntu:8.10/intrepid)
Conf djview4 (4.3-5 Ubuntu:8.10/intrepid)
Conf djvulibre-desktop (3.5.20-7ubuntu3 Ubuntu:8.10/intrepid)
Conf djvulibre-plugin (3.5.20-7ubuntu3 Ubuntu:8.10/intrepid)
Conf seamonkey-browser (1.1.12+nobinonly-0ubuntu1 Ubuntu:8.10/intrepid)
Conf seamonkey-gnome-support (1.1.12+nobinonly-0ubuntu1 Ubuntu:8.10/intrepid)

```

Why is djview4 trying to pulling a browser? I understand about the Netscape/Mozilla plugin, but (1) I don't care for it (2) shouldn't firefox, using similar engine, be sufficient?

Is there anyway to just get the viewer?

---

