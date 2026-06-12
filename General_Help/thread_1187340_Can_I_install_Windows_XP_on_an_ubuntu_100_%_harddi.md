---
title: "Can I install Windows XP on an ubuntu 100 % harddisk ?"
date: 2009-06-14
forum: General Help
---

### Post by Jønne on 2009-06-14
Hallo, my name is Jønne, and I am from Denmark.

I have a extern hard-disk, where is installed ubuntu 9.04 100 %.

Now I want to install Windows XP on the half of it.

500 GB extern harddisk.

But:

I guess I must use gparted first to erase ubuntu - correct?

Or can I install Windows XP and then install ubuntu again?

I am a bit confused, and would like a good advice, please.

Best Wishes and good Sunday from Jønne in Denmark

---

### Post by ActiveFrost on 2009-06-14
Both options will work - use gparted to free up some space or install Windows XP ( and use it's built in partitioning to leave some free space for Ubuntu ).

---

### Post by TeoBigusGeekus on 2009-06-14
You can install winxp but it will make your grub disappear.
Check out this page on how to get it back:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by mikewhatever on 2009-06-14
> **Jønne said:**
> 

I guess I must use gparted first to erase ubuntu - correct?

Or can I install Windows XP and then install ubuntu again?

I am a bit confused, and would like a good advice, please.

Best Wishes and good Sunday from Jønne in Denmark

You need to resize one of the existing partitions to make space for XP. Erasing and reinstalling Ubuntu is not necessary.
It's also worth mentioning that installing Windows on an external HDD doesn't seem to be a trivial matter. I have no first hand experience, but a google search turned up a page that looks far from user friendly. [http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

### Post by Zimmer on 2009-06-14
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

This guide may be of help...

---

### Post by Cheesemill on 2009-06-14
Just to re-iterate, it is **alot** of hard work to get Windows to install on an external drive (in fact Microsoft say it can't be done).

I have done it before using the above link ([http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)) but give yourself several hours to hack your Windows disk and install.

It's not much fun and the performance isn't very good, I got rid of my external Windows install after a day or two.

---

### Post by Jønne on 2009-06-16
Thanks a whole lot for your help and good answers !

:KS

Jønne

---

