---
title: "Beryl Crash"
date: 2007-02-02
forum: Desktop Environments
---

### Post by oliviacond on 2007-02-02
This is what happen after I run beryl-manager
> 
PC:~$ beryl-manager
PC:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed

** (beryl-manager:7040): WARNING **: Beryl caught deadly signal 11
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

PC:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800021 (Music Play)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by jd65pl on 2007-02-02
Beryl isn't a topic for beginners, try asking somewhere more appropriate or on the beryl forums.

---

### Post by jordanmthomas on 2007-02-02
The error says you're getting a segfault and that ~/.fonts.conf is malformed
Try renaming fonts.conf temporarily and restarting beryl

(though it looks as if it might be crashing before that even, so you will need to wait until the issue is resolved in svn probably)

---

### Post by chalewa on 2007-02-02
I am having the same issue...


I just installed the newest version today...

---

