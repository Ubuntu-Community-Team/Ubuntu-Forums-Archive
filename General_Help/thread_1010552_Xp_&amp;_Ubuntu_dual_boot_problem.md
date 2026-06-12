---
title: "Xp &amp; Ubuntu dual boot problem"
date: 2008-12-13
forum: General Help
---

### Post by Josey on 2008-12-13
I've been using an XP and Ubuntu dual boot for some time.  XP has been having problems and I need to reinstall it.  When setup run it is not detecting my ntfs partition properly.  It is a 39gb partition and XP setup thinks it is 132gb and (unknown format).

Obviously I don't want to just let it format 132gb on this disk as it is likely it will screw up my ubuntu partition.

Does anyone know why it might be having problems detecting the correct partition?

---

### Post by taurus on 2008-12-13
You can use gparted (install it if you don't have it in System -> Administration) and format that windows partition to ntfs filesystem.  Hopefully, windowns will detect it now.  And of course, windows will wipe GRUB off MBR so you won't be able to boot Ubuntu.  Therefore, you need to reinstall GRUB to MBR.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Josey on 2008-12-13
That was a logical suggestion but I'm still getting 132gb (unknown) in setup after formatting it and trying again.  :(

---

### Post by taurus on 2008-12-13
Can you post the output of this command from a terminal in Ubuntu?

```
sudo fdisk -l
```

---

### Post by Josey on 2008-12-13
Sure thing.  :)

```

/dev/sda1               1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       11862    54323797+  83  Linux
/dev/sda3           11863       38910   217263060    f  W95 Ext'd (LBA)
/dev/sda5           11863       38643   215118351   83  Linux
/dev/sda6           38644       38910     2144646   82  Linux swap

```

---

### Post by Josey on 2008-12-14
No ideas?  anyone?

---

### Post by TeXtonyx on 2008-12-14
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
Especially page 4.

You have Linux installed first, this is supposed to work as long
as you have an XP install disk with Service Pack 1 slipstreamed. 
Earlier versions of XP have a 137GB limit. How big is your drive?

---

### Post by Josey on 2008-12-14
300gb... that may be the problem.  Thanks

---

### Post by TeXtonyx on 2008-12-14
> **Josey said:**
> 300gb... that may be the problem.  Thanks

[http://apcmag.com/how_to_create_a_bootable_xp_sp3_cd.htm](http://apcmag.com/how_to_create_a_bootable_xp_sp3_cd.htm)

"With XP SP 3 now released, here's how to slipstream the service 
pack into your existing install CD. The big benefit? Serial 
number-free reinstalls of XP. 

Page 1 - Intro HOW TO: create a bootable XP SP3 CD

It’s been a while since anyone’s had to slipstream a Windows XP 
service pack, but seeing as how SP3 is now available, we thought 
we’d do a refresher course."

---

### Post by Josey on 2008-12-14
Thanks.  Reinstalling with a slipstream cd fixed it for me.  :)

Now I just need to figure out how to get it to mount the partition in ubuntu.

Many thanks :)

---

