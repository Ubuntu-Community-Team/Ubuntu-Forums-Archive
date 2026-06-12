---
title: "Dual booting XP after 9.10"
date: 2009-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Albertint on 2009-12-25
OK, so I'm having a small dilemma here:

So I want to install XP on top of my Ubuntu installation, so I've found [this]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1") guide to do so. Problem is, I'm trying to figure out how to backup the GRUB boot-loader. I look for this:

```
[COLOR=#ff0000]**sudo gedit /boot/grub/menu.lst**[/COLOR]
```But it turns up blank, and looking through that specified folder, non-existent. What am I doing wrong?

UPDATE: I also found [this]("http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/"). Can this help, any?

---

### Post by Albertint on 2009-12-25
OK, I've got a new idea. First, I'm going to partition some free space on my hard drive, then install XP on that unallocated space. Second, I'm going to use a grub super disk, and somehow use it to fix my grub loader. How can I carry this out without foiling things?

Just so I don't confuse anyone, I'm going to state my tools:
Parted Magic
Super Grub Disk
XP Install Disk
Inspiron 1525 laptop

---

### Post by oldfred on 2009-12-25
If you have a new install of Karmic not an upgrade you have grub2 not grub legacy. Grub legacy had menu.lst and grub2 uses grub.cfg that you do not edit. But grub2 is very good at finding other operating systems so after you restore grub2 just run this:

sudo update-grub

Do not use supergrub for grub2 repairs, it is good for grub legacy but has not yet been updated yet (as far as I know).

See this for restoring grub2, you will need your Karmic install liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Albertint on 2009-12-26
Cool, I'll try your information, thanks. It was starting to get confusing with all GRUB revisions. Yes, I'm using a fresh install of Karmic, not an update.

---

### Post by Gemu on 2009-12-27
I'm having the same problem. Grub legacy was booting windows xp fine on my 2nd hd 1st partition. After a fresh install of Ubuntu 9.10 on sda1 I now have grub2 and xp won't boot unless I change the order of the drives in the BIOS. I like windows on my second HD 1st partition so its MBR never gets over written.

I have tryed both of these menu entrys to no avail

menuentry "WinXP" {
set root=(hd1,1)
insmod chain
chainloader +1
}

menuentry "Windowsxp" (on /dev/sdb1) {
insmod ntfs
set root=(hd1, 1)
search --no-floppy --fs-uuid --set 77CE6D8C732ECE91
drivemap -s (hd0) $(root)
chainloader	+1
}
    

Any suggestions would be appreciated.

---

### Post by Gemu on 2009-12-27
I found the problem. Somehow I had gotten an l at the top left of 40)_custom and update-grub2 couldn't execute the /bin/sh

---

