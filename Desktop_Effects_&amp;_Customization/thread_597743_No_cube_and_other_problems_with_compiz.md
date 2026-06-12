---
title: "No cube and other problems with compiz"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by bailout on 2007-10-30
Trying to get compiz working. I installed 

compiz-kde
compiz-fusion plugins
settings manger
emerald

I started it by just typing compiz into konsole. It is working to some extent as I get the window decorations and some minor effects and wobbly windows works. However, nothing happens if I press ctrl + delete. I I have ticked the 'enable cube' in the settings. I also have the problem that with tiled windows I don't seem able to bring a lower one to the top. If I click on a bottom window the focus goes to it and I can even type in it but the windows that are on top remain there. The only way I can get to a lower window is to minimise the ones on top.

My graphics card is an intel 945gm onboard which ran beryl ok. However, when I typed beryl into konsole I got these error messages, although it does work, at least partly.

Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

thanks

---

### Post by bailout on 2007-10-31
Any ideas before I give up?

---

### Post by StormRoBoT on 2007-10-31
i have no cube also here.. just install the ubuntu 7.10

last time i used 7.04 there are option to enable the cube option

---

### Post by moon2js on 2007-11-01
I get the feeling after reading [another thread]("http://ubuntuforums.org/showthread.php?t=593402") that the cube isn't enabled by default on Gutsy. When I drag a window to the side of the screen onto a new workspace, the whole screen shifts to the new space visually, but no cube.

According to aforementioned thread, compiz-settings-manager is need for the cube effect.

```
sudo apt-get install compiz-settings-manager
```

...or via Synaptic install compiz-settings-manager and then newly available visual options should be in "System > Preferences > Advanced Desktop Effects Settings."

---

