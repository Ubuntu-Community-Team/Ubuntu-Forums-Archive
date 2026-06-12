---
title: "No camera detected"
date: 2009-06-13
forum: General Help
---

### Post by akernan on 2009-06-13
I have ubuntu and kernel 2.6.28-11, I use Fluxbox.  When I import photos with gthumb it says 'No Camera Detected'.  I get the following with lsusb...

tony@tony-laptop:~$ lsusb
Bus 001 Device 009: ID 04b0:0413 Nikon Corp. D40 (mass storage mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Why can I not import photos?

---

### Post by akernan on 2009-06-14
I just read the Jaunty bug post and found the new libgphoto2 library, but when I compile it I get the following error...
> configure: error: cannot compile and link against libltdl
libgphoto2 requires libltdl (the libtool dl* library),
but cannot compile and link against it.


What does this mean?  Can anyone help me with this?

---

### Post by unutbu on 2009-06-14
According to this thread: [http://ubuntuforums.org/showthread.php?t=592539&page=2](http://ubuntuforums.org/showthread.php?t=592539&page=2) (and in particular, millguy's post: [http://ubuntuforums.org/showpost.php?p=4327704&postcount=14](http://ubuntuforums.org/showpost.php?p=4327704&postcount=14))
you need to set the camera's mode to PTP rather than MTP.

If you are using Ubuntu version 8.10 or later, then also check ~/.gvfs. Your camera's files may already be mounted there.

---

### Post by akernan on 2009-06-14
That did it.

Thanks,
Tony

---

