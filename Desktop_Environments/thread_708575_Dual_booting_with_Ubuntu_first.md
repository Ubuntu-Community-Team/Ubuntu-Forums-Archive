---
title: "Dual booting with Ubuntu first"
date: 2008-02-26
forum: Desktop Environments
---

### Post by gforcing on 2008-02-26
Hello all - I've got a bit of an issue.

I've currently got Ubuntu Gutsy installed on my laptop, and just learned that I need to be able to use MS Visual Studio 2005 this summer. The problem is (from what I've heard) VS2k5 doesn't play nice with VMWare, so I'd like to try to dual-boot. However, I'll be going backwards - every other dual-boot guide I've found has the user configuring dual-boot from XP, rather than the other way 'round. 

What I want to know is, can I set up a dual-boot system with XP and Ubuntu if I already have Ubuntu installed, and if so, how?

Thanks!

---

### Post by luisromangz on 2008-02-26
I used VS2005 in VMWare and it worked perfectly, if you provide the Windows guest system with enough ram (and enough is not that much actually).

---

### Post by gforcing on 2008-02-26
> **luisromangz said:**
> I used VS2005 in VMWare and it worked perfectly, if you provide the Windows guest system with enough ram (and enough is not that much actually).

How much would you consider enough? Mind, I'm trying to get this working on a laptop with a mediocre (at best) processor and about 1.25GB of RAM.

Also, how did you get it working with VMWare? Like I said, from what I've read it doesn't work well, but if you could get it to work, I'd like to know how I could do the same.

---

### Post by luisromangz on 2008-02-26
Around 400-500mb for the virtual machine was enough. Visual Studio works in VMWare as it works in a real machine, I don't remember any problems. I have colleagues running WinXP + VS 2008 in VirtualBox (an alternative software to VMWare) nowadays, and they don't have any problems neither.

---

### Post by stirred on 2008-03-11
Deas anybody knows how to configure DUAL BOOT (say ubuntu/xp) ona box where UBUNTU has been installed FIRST? Thanks a lot!

---

### Post by #Reistlehr- on 2008-03-11
Yeah its simple, install XP on a seperate partition, Use fdisk in ubuntu to resize the partitions so you have enough space.. Install XP, then when its finished, you'll have to use the ubuntu cd to reinstall grub, since XP overwrites the mbr..

ope it helps

---

### Post by sandysandy on 2008-03-11
u can also use Super Grub Disk to reinstall GRUB once XP overwrites MBR during installation.

have tried it out successfully.

regards

---

### Post by jlabomb on 2008-05-01
I am trying to do the same thing. I used this article.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

only problem is that my windows only sees the hard drive as one big hard disk not partition like I setup in gparted. I have a 500 GB WD drive and set 30 GB for XP but when XP sees the disk no partitions just one 130GB drive. I can't seem to hide my partition that has Ubuntu on it. Gparted won't let me check it for some reason. Any help is appreciated. Thanks.

[SCALOS - I search the net so you don't have to]("http://scalos.webs.com")

---

### Post by Fixman on 2008-05-01
> **jlabomb said:**
> I am trying to do the same thing. I used this article.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

only problem is that my windows only sees the hard drive as one big hard disk not partition like I setup in gparted. I have a 500 GB WD drive and set 30 GB for XP but when XP sees the disk no partitions just one 130GB drive. I can't seem to hide my partition that has Ubuntu on it. Gparted won't let me check it for some reason. Any help is appreciated. Thanks.

If you follow the instructions step by step then this shouldnt happen.

---

### Post by jlabomb on 2008-05-02
I must be missing something on the instructions. I use gparted to shrink my partition 30 GB for windows. Then I load the windows xp cd. But when it comes to the select partition screen there is only one 130 GB drive available. The tutorial says that it will show my Ubuntu partition and does not so I don't want to erase that. I may just try to find a cheap hard drive to install it on. 


[SCALOS - I search the net so you don't have to]("http://scalos.webs.com")

---

