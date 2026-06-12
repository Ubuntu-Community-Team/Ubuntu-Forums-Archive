---
title: "Cant load vista after installing xp"
date: 2009-03-19
forum: General Help
---

### Post by bimi on 2009-03-19
Can somebody please help me? 

I have 2 hard disk, the first one has ubuntu and vista, the second hard disk has xp; the problem is grub only detects the xp, how do configure grub to boot into vista?

[B][I]
Chronologi of events:[/I][/B]

Disk 1:
I installed vista.

I installed ubuntu.

I can dualbot ubuntu and vista.
----
Then Disk 2:

I installed xp.

Now I can only boot to xp.

------------

***Then, i restored grub:***

With this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

Boot with ubuntu live cd,

with Grub i did:

grub> find /boot/grub/stage1
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

Now I can only boot with ubuntu and xp but _not_ vista.

--------------------------------------

***Heres fdisk -l:***

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x288c10d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7650    61440000    7  HPFS/NTFS
/dev/sda2            7651       11296    29286495   83  Linux
/dev/sda3           11297       23697    99611032+   5  Extended
/dev/sda4           23698       27344    29294527+  83  Linux
/dev/sda5           11297       11539     1951866   82  Linux swap / Solaris
/dev/sda6           11540       23697    97657856    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x392f6afe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sdb2            6529       15666    73400985    5  Extended
/dev/sdb5            6529       15666    73400953+   7  HPFS/NTFS
---------------------------------------------------

***The /boot/grub/menu.lst***

default		0

timeout		10

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e2ab84c0-9129-4178-9185-631e070d7bd4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e2ab84c0-9129-4178-9185-631e070d7bd4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e2ab84c0-9129-4178-9185-631e070d7bd4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e2ab84c0-9129-4178-9185-631e070d7bd4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e2ab84c0-9129-4178-9185-631e070d7bd4
kernel		/boot/memtest86+.bin
quiet

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

--------------------------------------------------

Thanks for your help [-o<

---

### Post by bimi on 2009-03-19
bump

---

### Post by plucky on 2009-03-19
This [link](http://ubuntuforums.org/showthread.php?t=740221&highlight=xp+vista+grub) might help.Never tried it so cannot personally say it will work.

Also search the [Tutorials and Tips](http://ubuntuforums.org/forumdisplay.php?f=100) sub-forum for How to restore windows bootloaders.

From what I have read,you have to use the Vista bootloader,which can recognize XP partition,but the XP bootloader cannot recognize a Vista partition.

Good Luck

;)

---

### Post by ruel- on 2009-03-19
I suggest, you fix the MBR / bootloader in Vista first, vista will recognize XP on it's boot..

then re-configure GRUB... :)

---

### Post by bimi on 2009-03-20
> **ruel- said:**
> I suggest, you fix the MBR / bootloader in Vista first, vista will recognize XP on it's boot..

then re-configure GRUB... :)

I tried this, now only Vista and XP is recognized. Grub is now overwritten with the Windows Bootloader, i can now boot vista and xp, but not ubuntu.

After asking around on the irc, someone told me that because i'm using two physical disc, and the two of them have windows on it, I will need to tell Grub to ***map*** it.

Something like this:

[http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap16]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap16")

Can anyone tell me how to map my OSes with Grub?

---

### Post by plucky on 2009-03-20
> Can anyone tell me how to map my OSes with Grub? 


This [link](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries) might help.Scroll down to "Windows Operating System Entries".

I think you will have to re-install grub and add the entry for the Vista boot loader to grub.Then use the Vista boot loader to select either XP or Vista.(But don't quote me on that)

Good Luck

---

