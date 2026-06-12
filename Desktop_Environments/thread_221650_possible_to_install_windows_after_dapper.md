---
title: "possible to install windows after dapper?"
date: 2006-07-23
forum: Desktop Environments
---

### Post by harty83 on 2006-07-23
Okay.  I am trying to get remote wakon lan to work on my Dell Optiplex gx240 which currently has dapper on it.  I have it enabled in BIOS but according to dell's support page, that won't work.  

> Although Remote WakeUp (RWU) is enabled in the System Setup (BIOS) program, Dell™ OptiPlex™ computers with the 3Com 3C905C (3C920) network interface controllers (NICs) do not respond to RWU commands if the computer is using the native 3C905C driver that comes with the Windows 2000 operating system.

OptiPlex computers may not respond to RWU commands because Remote WakeUp (also called Wake on LAN) is not enabled on the Windows 2000 3Com 3C905C native driver.

So they give directions here to install a specific driver to get this to work.  [http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?docid=7644DF30E2D14880BE9F68F101C51830&c=us&l=en&s=gen](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?docid=7644DF30E2D14880BE9F68F101C51830&c=us&l=en&s=gen)

Is there a way to do this in linux?  

If not, I have a two harddrives.  Can I install windows xp on my second harddrive so I can perform this operation?  My initial thought is yes but it will mess up grub.  So how do I do this without messing up my grub installation?  Or if there is no way of getting around messing up grub, how do I fix it after installing windows?

Thanks!

---

### Post by Jhongy on 2006-07-23
I'm afraid I can't help you with the first question, but I can with the second - as I jsut got done with it myself this weekend.

Yes, it most likely will mess up grub. But you can easily fix it by using the live CD, mounting the partition where your /boot directory is, and then doing grub-install /dev/hda0, or wherever your drive is.

By the way, I have 3 HDDs, and had untold troubles installing WinXP - it kept on insisting on installing the boot sector and boot files on the other disk, which gave me untold problems when I destroyed that partition later and couldn't get XP to boot. If the Win installer asks you to format TWO partitions for it, instead of just one, then you may want to disconnect one of the HDDs for the install.

---

