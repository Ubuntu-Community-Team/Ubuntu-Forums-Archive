---
title: "Automatically restart in XFCE 4.8"
date: 2011-11-13
forum: Desktop Environments
---

### Post by mr.suchy on 2011-11-13
Hi,

One again I write here bcs I have a problem with my xbuntu. I use 285.05.09 Nvidia driver and XCFE 4.8 I guest. Sometime or should I say often I have restart XCFE - automatically without any command. When I check log, sys.log, message.log and search any error or failed I don't see anything at the time when I had XFCE crash. Where can I check or what can I do to fix this ?

Best regards.

---

### Post by ankspo71 on 2011-11-13
Hi,
Look in your home folder for the hidden file called ".xsession-errors", and also look inside the system folder /var/crash to see if any crash dump files have been created.

If you still don't find any errors, you could try enabling apport to see if apport can catch the crash for you, and you can also report the crash with this tool at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu). Here is how to enable apport: [https://wiki.ubuntu.com/Apport#How_to_enable_apport](https://wiki.ubuntu.com/Apport#How_to_enable_apport)

Hope this helps.

---

### Post by mr.suchy on 2011-11-14
Hi

Firstly, thanks for replay. Secondly I have this problem one again about 10:16 p.m (22:16 my time) but when I look at the /var/crash is was empty (any dump). I check .xsession-errors like U said and I don't see anything at all (which may affect). 

If somebody can look at my log (attachment) I'll be grateful.

Best Regards:P

edit

I check Xorg.0.log and I found this:
```
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(EE) Nov 14 22:16:02 NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(WW) Nov 14 22:16:03 NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) Nov 14 22:16:03 NVIDIA(0):     back to legacy PCI mode.
```
this is time when I had this automatically restart. What should I do with this ? Install older driver ? 

Sorry for my language, corect me if I say something stupid :lolflag:

---

