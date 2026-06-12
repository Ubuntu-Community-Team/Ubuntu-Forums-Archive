---
title: "Win XP partition won't boot after installation."
date: 2008-07-09
forum: Desktop Environments
---

### Post by cyberick on 2008-07-09
Hello, folks, I think I need your help. I installed Ubuntu 8.04 on my home desktop and it's working perfectly. The Win XP partition, however, isn't even accessible (actually I can access the Win XP partition through Ubuntu, but it won't boot!). I really need access to the Windows partition because I'm not the only one using this computer!


In summary, the status is:

-Type of installation: Dual-boot (windows xp & ubuntu)
-Ubuntu partition: Working perfectly
-Windows XP partition: Not bootable, only accessible through Ubuntu. It doesn't shows any errors; it only stays at "Starting up..."

What I've done:

-I used the command **sudo fdisk -l** which outputted this:


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfadbfad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5665    45504081    7  HPFS/NTFS
/dev/sda2            5666        9729    32644080    5  Extended
/dev/sda5            5666        9556    31254426   83  Linux
/dev/sda6            9557        9729     1389591   82  Linux swap / Solaris
```




Then I took a look at the grub menu.lst and it seems to be ok. This is part of the menu.lst file:

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5820816b-f221-4f10-9519-e253c338991a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5820816b-f221-4f10-9519-e253c338991a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```




-I tried fixing the MBR with the Windows CD and it didn't work; it outputted an error after rebooting. After this, I booted with the Ubuntu live CD and repaired Grub. So now I'm at the starting point! :mad:



Thanks a lot in advance;

~Cyb

---

### Post by logos34 on 2008-07-09
boot the xp cd again (>recovery console) and run **chkdsk /r**

---

### Post by cyberick on 2008-07-09
Still the same results. :( Any other recommendations before I reinstall Windows (my last option)?


Thanks again for your time and patience!

---

### Post by DizzyTech on 2008-07-09
Don't reinstall just yet.  If anything, just do a repair install.

If you're only seeing "Starting up..." this means that Windows' bootloader, NTLDR is not starting at all.  Make sure to look for ntldr, autodetect.bat, and boot.ini in your Windows root.

---

### Post by cyberick on 2008-07-12
It seems like the Windows root contains the necessary files to boot:

```

cyberick@cyberick-desktop:/media/disk$ ls
AUTOEXEC.BAT
Automap
bootex.log
boot.ini
CONFIG.SYS
Documents and Settings
hiberfil.sys
IO.SYS
MSDOS.SYS
MSOCache
NTDETECT.COM
ntldr
Program Files
RECYCLER
rollback.ini
ScanSectorLog.dat
sqmdata00.sqm
sqmdata01.sqm
sqmnoopt00.sqm
sqmnoopt01.sqm
System Volume Information
WINDOWS

```

---

### Post by DizzyTech on 2008-07-13
Sorry, but looks like it is one of those terrible inexplicable errors.  Reinstall XP using the repair option (by going through the install routine as regular, but make sure it says repair after the license agreement) and then restore the GRUB loader from Ubuntu like you already have.  Make sure your /boot/grub/menu.lst points to the right partition, and you should be in business.

---

### Post by sandysandy on 2008-07-13
have u tried booting windows with SGD (Super Grub Disk)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

regards

---

### Post by WizMdic on 2008-07-14
Hello,

Try the steps on this website:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Works great with Vista and I think there is a setup with XP also. 

Good luck!

---

