---
title: "Windows XP dual boot"
date: 2009-02-09
forum: General Help
---

### Post by ananta.c on 2009-02-09
Hi all,

I googled lot of forums regarding xp dual boot, all the discussion go beyond installation. they talk about BIOS... bla bla bla....

I am 100% windows user trying to change and got installed xubuntu and kept 20 GB unpartitioned. now when I tried to install windows in it , it screwed up my xubuntu boot. I got it recoved back to xubuntu with some simple steps,but I don't find easy way to do dual boot with with windows xp. If some one can hellp me in simple steps it will be great

Recap: I have 160 GB HDD with 20 GB free space and I want to dual boot with xp, please give me step by step easy process ( in layman steps) , don't use any sort of techical jargons, if possible please provide screenshots too

---

### Post by DougieFresh4U on 2009-02-09
I thought that Windows was to be installed first for a dual boot?

---

### Post by ananta.c on 2009-02-09
Well I did other way :)

> **DougieFresh4U said:**
> I thought that Windows was to be installed first for a dual boot?

---

### Post by williane on 2009-02-09
Yep, Windows doesn't like to have competition. Ubuntus still there, windows just changed the grub bootloader so your comp boots straight to Windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hansdown on 2009-02-09
Hi ananta.c.

Windows does prefer to be the first os installed. 

Here is a good tutorial.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by zeealpal on 2009-02-09
Boot from a live CD, open a terminal and use the command "sudo grub-install" and specify the hard disk location

---

