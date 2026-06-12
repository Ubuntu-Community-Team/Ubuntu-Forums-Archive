---
title: "Grub Error 21 help!"
date: 2009-04-19
forum: General Help
---

### Post by KritSandvich on 2009-04-19
Hello,

(The version of Ubuntu I'm using is Jaunty Jackalope RC)
Yesterday I decided to make a full install of Ubuntu onto my flash drive using the live CD. It was successful, but now I can't boot into Windows (I don't dual boot, so XP is all I have on this computer) because GRUB gives me "ERROR 21". I tried the following:
```

grub-install /dev/sda2 

```
(My NTFS partition is in sda2, and is intact)
But it tells me: 
```

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

Then I tried installing ms-sys and calling:

```
ms-sys -m -f /dev/sda2
```

That worked without errors, but it didn't solve the problem (I got the same error)

Can anyone help?
Thanks in advance.

EDIT:
Now I have another problem. I tried to mount /dev/sda2 a couple seconds ago, but it wasn't in 'Places'; so I ran GParted and it says the file system of /dev/sda2 is 'unknown'.

---

### Post by KritSandvich on 2009-04-19
Bump!
Please someone help! :(

---

### Post by KritSandvich on 2009-04-19
Double bump!
Is this in the wrong forum or something?

---

### Post by ajgreeny on 2009-04-19
If you have removed the usb flash drive, put it back and try again.  Grub will probably be on the MBR of windows, unless you changed anything at installation, and it is trying to find the /boot/grub/menu.lst file which is on the flash drive.

---

### Post by KritSandvich on 2009-04-19
Thanks for the reply!

The flash drive was plugged in when I got the error, unfortunately.

---

### Post by KritSandvich on 2009-04-19
Actually, ignore my last post.

I tried it again, and GRUB loaded and I got a menu. But when I selected Windows XP, I got an "Invalid Partition Table" error. How do I fix this?

---

### Post by meierfra. on 2009-04-19
> 
grub-install /dev/sda2
ms-sys -m -f /dev/sda2
Each of those command  destroy the XP boot sector. To fix it

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"BackupBS"
Type "Y" to confirm.

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.

---

