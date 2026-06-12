---
title: "Gutsy and X1300: Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by DrQuincy on 2007-10-18
I upgraded to Gutsy this morning.  The graphics drivers most certainly are not out-of-the-box - it has totally trashed my display.

I have a Radeon X1300 and I get this output:

```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

Any ideas how I imght fix it?  I've tried installing the ATI driver with Envy but that crashed it (black screen).

If I go to the Restricted Drivers Manager even though the box is checked for the ATI card it has a red icon and says not in use.

---

### Post by Thangalin on 2007-10-18
Hi, DrQuincy.

You are not alone. There are several things you can try to fix it, but I'll be the first to point out that they might not work.

1) Append the LVDS option and AIGLX options into **/etx/X11/xorg.conf** -- as follows:

```
Section "ServerFlags"
  Option      "AIGLX" "off"
  Option      "LVDSBiosNativeMode" "false"
EndSection
```

The AIGLX option may be superfluous. Also, try putting **Option      "LVDSBiosNativeMode" "false"** in the "Device" section, instead. (The documentation was not clear on where this line should be placed.)

2) Try to reconfigure the xorg configuration file using **dpkg-reconfigure xserver-xorg** -- you will need to find your horizontal and vertical refresh rates for your monitor.

3) Disable the "fglrx" module in **/etc/default/linux-restricted-modules-common** by setting the last line in the file to:

```
DISABLED_MODULES="fglrx"
```

Be sure to include any other disabled modules that may already be listed (separated by a space).

4) a) Uninstall the "default" bundled ATI drivers that come with Ubuntu: **sudo apt-get uninstall xorg-driver-fglrx**

4) b) Install the driver that comes from ATI. [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")

4) c) Instructions at: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

5) Keep an eye on this thread: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716")

6) Consider using the following (also in **/etc/X11/xorg.conf**); your **Identifier** and **BusID** may vary:
```
Section "Device"
  Identifier  "ATI RADEON X1300"
  Driver      "fglrx"
  Option      "VideoOverlay" "on"
  Option      "OpenGLOverlay" "off"
  BusID       "PCI:1:0:0"
EndSection
```

7) Lastly, disable the **Composite** option:
```
Section "Extensions"
  Option      "Composite" "Disable"
EndSection
```

If you get it to work, let us know what you did that finally fixed it. The only thing I can do at the moment is replace "fglrx" with "vesa" to get into KDE, which avoids fglrx altogether (and produces the same fglrxinfo message as you get). Otherwise, black screen of doom.

---

### Post by DrQuincy on 2007-10-19
Thanks for your reply.

I've tried all that that and still nothing.  In fact, I'm down to 800 x 600 now!  I was better off not upgrading.  Al least under Fesity although the ATI driver never worked I had 1680 x 1050.

How can I get the LCD to its native resolution?

---

### Post by Thangalin on 2007-10-19
> **DrQuincy said:**
> How can I get the LCD to its native resolution?

Buy an nVidia-based card.

Okay, so maybe that's not an option.

To get your native resolution, edit **/etc/X11/xorg.conf** ... change "fglrx" to "vesa". That, at least, should get you back to full resolution. You may have to rerun the reconfigure program (from step 2).

Good luck!

---

### Post by DrQuincy on 2007-10-20
Whenever I reconfigure X server I end up having to use vesa because nothing else works.  Is vesa capable of 1680 x 1050?  I may be wrong but I thought it was limited.

---

