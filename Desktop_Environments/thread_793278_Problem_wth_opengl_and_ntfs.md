---
title: "Problem wth opengl and ntfs"
date: 2008-05-13
forum: Desktop Environments
---

### Post by szemy on 2008-05-13
Hi every one!
I have two small issues with my xubuntu box:
1.)Opengl isn't working
glxinfo output:

name of display: :0.0
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7775767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb77758b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb79011bd]
#3 /usr/lib/libGL.so.1 [0xb7dce22b]
#4 /usr/lib/libGL.so.1 [0xb7dcd87a]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7775767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb777581e]
#2 /usr/lib/libX11.so.6 [0xb7900518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb78f70a6]
#4 /usr/lib/libGL.so.1 [0xb7dcddb1]
glxinfo: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
szemy@szemy-desktop:~$ 

2.)I am dualbooting the box, but don't really want to use windows anymore. The problem is that I can't excess the windows partition. 'Mount' and 'ls /dev/' and even '/etc/fstab' doesn't list it! What could be the problem? 

Thank you very much for youre time
Thomas

---

### Post by szemy on 2008-05-14
Could be that this isn't a xubuntu only problem?

---

### Post by jakon on 2008-05-14
@NTFS:
Ubuntu has windows disks listed under Places, doesn't Xubuntu have something similar?

But you can always mount your windows disk manually. In a terminal```
sudo mkdir /media/win
sudo mount -t ntfs-3g /dev/sda1 /media/win
```(This assumes that your windows disk is /dev/sda1. If your windows disk isn't /dev/sda1 it will just fail. Execute ```
sudo sfdisk -l /dev/sda
``` in a terminal, look for NTFS on the right and use the correct /dev/XYZ from the leftmost column.)

---

### Post by szemy on 2008-05-14
Thanks!
It really worked. Don't know why this isn't automatic.
Will this stay after restart?
Thomas

---

### Post by jakon on 2008-05-14
No, this won't persist after a restart.

But this will automount the partition on boot:```
sudo -s
echo "/dev/hda1 /media/win ntfs-3g 0 0" >> /etc/fstab
```

---

