---
title: "Compiz in Debian 5.0 with Intel GMA 3100"
date: 2009-02-15
forum: Debian
---

### Post by noway on 2009-02-15
!! PROBLEM SOLVED !!



I'm trying to get Compiz working on Debian 5.0 with Intel GMA 3100. I've installed **compiz** and **libgl1-mesa-dri**, then I restarted X with ctrl+alt+backspace and did **compiz --replace** in terminal which gave me this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Could not open network socket
/usr/bin/compiz: line 393:  9053 Segmentation fault      ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS





SOLUTION

In terminal:

aptitude install compizconfig-settings-manager libcompizconfig0 python-compizconfig

compiz --replace


and according to [http://wiki.debian.org/Compiz](http://wiki.debian.org/Compiz) 

echo "export WINDOW_MANAGER=/usr/bin/compiz" >> ~/.gnomerc

to make it start automatically.


Install compiz-fusion-plugins-main and compiz-fusion-plugins-extra for more plugins.

---

