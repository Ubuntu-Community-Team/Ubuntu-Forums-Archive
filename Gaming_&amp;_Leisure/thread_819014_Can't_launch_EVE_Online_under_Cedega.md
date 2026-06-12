---
title: "Can't launch EVE Online under Cedega"
date: 2008-06-05
forum: Gaming &amp; Leisure
---

### Post by dppowell on 2008-06-05
Running 64-bit Hardy on a HP dv9700t notebook with NVidia 8400GS video:

```
dave@gewgaw:~$ eve
Single-user install...
This is the update checker... 
Running /home/dave/.cedega/.updater/cedega_updater.py
Running... /home/dave/.cedega/.ui/runGUI
dave@gewgaw:~$ X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3585
  Current serial number in output stream:  3587
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3592
  Current serial number in output stream:  3597
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3598
  Current serial number in output stream:  3601
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3642
  Current serial number in output stream:  3647
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  62 (X_CopyArea)
  Resource id in failed request:  0x760034d
  Serial number of failed request:  3646
  Current serial number in output stream:  3647
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0x56f39767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x56f3981e]
#2 /usr/lib32/libX11.so.6 [0x5637c518]
#3 /usr/lib32/libX11.so.6(XESetCloseDisplay+0x31) [0x5635f8d1]
#4 /usr/lib32/libGL.so.1 [0x56215b69]
#5 [0x7804b1e0]

```

When I run glxinfo, direct rendering is disabled.  I'm wondering whether that's my problem, and if so, how I can enable it.

*Edited to add:*
I found the solution in this post:

[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

The only tweak I needed to make was in the /usr/bin/nonXgl specified by that howto.  I had to use ```
DISPLAY=":0"
``` where Arnieboy used ```
DISPLAY=":93"
```.

The rendering of my spaceship and character thumbnails is messed up, but the game is playable.

---

