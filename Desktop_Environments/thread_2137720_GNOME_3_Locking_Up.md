---
title: "GNOME 3 Locking Up"
date: 2013-04-21
forum: Desktop Environments
---

### Post by ceil210 on 2013-04-21
I use Ubuntu 12.04:  I use the GNOME 3 shell.  About every three to four hours, GNOME 3 locks up on me.  I don't get any error messages; my system just freezes.  I have no idea how to fix this.  Any help would be nice!

---

### Post by rrich1974 on 2013-04-22
but still, how is the behavior using unity 3D, is it better?

---

### Post by ceil210 on 2013-04-22
Refresh my memory, is Unity3D the default Ubuntu shell?  I'll try to get used to it and take it for a test run and report back :-)

---

### Post by markbl on 2013-04-22
> **ceil210 said:**
> I use Ubuntu 12.04:  I use the GNOME 3 shell.  About every three to four hours, GNOME 3 locks up on me.  I don't get any error messages; my system just freezes.  I have no idea how to fix this.  Any help would be nice!

Completely freezes? Does the mouse still move? Can you remote ssh in while it is locked up? You should state your video card (lspci | grep -i vga). If you have intel video then you may have the xorg problem introduced in recent ubuntu updates, see [http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691).

---

### Post by ceil210 on 2013-04-22
> **markbl said:**
> Completely freezes? Does the mouse still move? Can you remote ssh in while it is locked up? You should state your video card (lspci | grep -i vga). If you have intel video then you may have the xorg problem introduced in recent ubuntu updates, see [http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691).


It doesn't *completely* freeze.  I can still use my terminal and mouse... gnome just gets "lazy".



**Edit:**
I have no idea on how to rollback on my kernel.... :-(

I also notice that relogging sort of fixes it.

As far as my card goes...

> alex@ubuntu:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

