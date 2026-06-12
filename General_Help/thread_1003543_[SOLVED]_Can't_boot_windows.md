---
title: "[SOLVED] Can't boot windows"
date: 2008-12-06
forum: General Help
---

### Post by anil7 on 2008-12-06
Hallo everyone. I know this is a common problem but I can't solve it on my own. I just installed ubuntu 8.10 in a partition in my first HD. Something must have went wrong and I can't boot windows. Each time I press enter on windows option in grub nothing happens. It just gets me back to grub menu. What went wrong?? 
here is my sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e853e85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   134994194    67497066    c  W95 FAT32 (LBA)
/dev/sda2   *   134994195   155701979    10353892+  83  Linux
/dev/sda3       155701980   156296384      297202+  82  Linux swap / Solaris

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1858bbd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   321669494   160834716    7  HPFS/NTF

And here is my menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		fc634e39-b4d9-4316-9d50-e38c7d71d4b0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fc634e39-b4d9-4316-9d50-e38c7d71d4b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		fc634e39-b4d9-4316-9d50-e38c7d71d4b0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fc634e39-b4d9-4316-9d50-e38c7d71d4b0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		fc634e39-b4d9-4316-9d50-e38c7d71d4b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fc634e39-b4d9-4316-9d50-e38c7d71d4b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		fc634e39-b4d9-4316-9d50-e38c7d71d4b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fc634e39-b4d9-4316-9d50-e38c7d71d4b0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		fc634e39-b4d9-4316-9d50-e38c7d71d4b0
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


Please help me!!!!

---

### Post by mikewhatever on 2008-12-06
Is Windows on the /dev/sda1 Fat32 partition, or is it on the second hdd- /dev/sdb1 ntfs? Do you get any errors when trying to boot Windows?

---

### Post by anil7 on 2008-12-06
in the first partition. Nope no errors. When I press the windows option it's like rebooting grub. Is there any chance that i could have deleted the master boot record file?

---

### Post by caljohnsmith on 2008-12-06
> **anil7 said:**
> in the first partition. Nope no errors. When I press the windows option it's like rebooting grub. Is there any chance that i could have deleted the master boot record file?
If Windows is on the first partition, then your Windows entry in your menu.lst should be fine. But if you get thrown back to the Grub menu when booting Windows, that usually means you accidentally installed Grub to the boot sector of the Windows partition at some point. To fix it, you'll need to boot your Windows Install CD, go to the "recovery console", and run:
```
fixboot
```
And then you should be all set. Let me know how it goes or if you run into more problems. :)

---

### Post by anil7 on 2008-12-06
I did this and after that I tried to boot windows and it says disk error.. Any ideas?

---

### Post by caljohnsmith on 2008-12-06
OK, sounds like you have more than one problem then with Windows, but we're making progress now that it sounds like Windows is at least trying to boot. I think it would be good to check your Windows partition to make sure it has the necessary boot files, so please post:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
cat /mnt/sda1/boot.ini /mnt/sdb1/boot.ini
```
Note "-l" is a lowercase L, not a one. We can work from there.

---

### Post by ASK87 on 2008-12-06
I had a similar problem earlier, when i had windows, I tried playing around with the drive numbers (hdx,x) and finally i got it. I dont know the real problem and neither i know if this will work. But before you do it, please make sure you back up the menu.lst.

---

### Post by anil7 on 2008-12-06
andreas@andreas-desktop:~$ ls -l /mnt/sda1 /mnt/sdb1

/mnt/sda1:
total 992
drwxr-xr-x   4 root root  32768 2008-01-12 14:52 adaptec
-rwxr-xr-x   1 root root      0 2008-01-12 13:58 autoexec.bat
-r-xr-xr-x   1 root root   4952 2001-11-27 12:00 Bootfont.bin
-rwxr-xr-x   1 root root    211 2008-01-12 13:51 boot.ini
drwxr-xr-x   7 root root  32768 2008-01-12 14:27 btmagic.pq
-rwxr-xr-x   1 root root      0 2008-01-12 13:58 config.sys
drwxr-xr-x   7 root root  32768 2008-01-12 13:42 Documents and Settings
drwxr-xr-x   3 root root  32768 2008-01-12 18:02 download
-rwxr-xr-x   1 root root    310 2008-09-17 20:06 index.html
-r-xr-xr-x   1 root root      0 2008-01-12 13:58 io.sys
drwxr-xr-x   4 root root  32768 2008-10-31 14:09 iPAQ
drwxr-xr-x   2 root root  32768 2008-01-12 14:52 Magenta
drwxr-xr-x  17 root root  32768 2008-06-05 21:25 matlab7
-r-xr-xr-x   1 root root      0 2008-01-12 13:58 msdos.sys
dr-xr-xr-x   3 root root  32768 2008-01-13 16:48 MSOCache
drwxr-xr-x   2 root root  32768 2008-05-11 17:19 netsim
-r-xr-xr-x   1 root root  47564 2004-08-03 20:38 ntdetect.com
-r-xr-xr-x   1 root root 251728 2004-08-03 20:59 ntldr
drwxr-xr-x  89 root root  32768 2008-01-12 13:57 Program Files
drwxr-xr-x   2 root root  32768 2008-01-12 18:05 Recycled
-rwxr-xr-x   1 root root  21493 2008-05-11 19:29 s16c
-rwxr-xr-x   1 root root    268 2008-08-26 21:12 sqmdata00.sqm
-rwxr-xr-x   1 root root    244 2008-08-26 21:12 sqmnoopt00.sqm
drwxr-xr-x   3 root root  32768 2008-01-12 14:03 System Volume Information
drwxr-xr-x   2 root root  32768 2008-10-30 17:16 temp
-rwxr-xr-x   1 root root      0 2008-02-04 19:27 _wdsuef.dmp
drwxr-xr-x 182 root root  32768 2008-01-12 13:38 windows
drwxr-xr-x  19 root root  32768 2008-11-04 15:15 xampp

/mnt/sdb1:
total 1208
drwxrwxrwx 1 root root   12288 2007-01-11 18:32 29f7d327d0245b59e93c
drwxrwxrwx 1 root root    8192 2007-12-10 04:21 BitComet
drwxrwxrwx 1 root root 1097728 2007-11-26 21:45 Config.Msi
drwxrwxrwx 1 root root   28672 2008-12-04 14:44 Downloads
drwxrwxrwx 1 root root   12288 2008-11-20 20:48 duth
drwxrwxrwx 1 root root   12288 2008-12-04 14:03 extra
drwxrwxrwx 1 root root    4096 2008-01-27 19:07 fortran
drwxrwxrwx 1 root root    4096 2007-11-22 19:10 gamez
drwxrwxrwx 1 root root       0 2008-11-11 14:04 Microsoft Visual Studio
drwxrwxrwx 1 root root    8192 2008-12-04 14:07 multimedia
drwxrwxrwx 1 root root    4096 2008-12-04 14:07 music
drwxrwxrwx 1 root root   36864 2008-11-19 16:45 my pictures
drwxrwxrwx 1 root root    4096 2007-09-08 21:17 programmata_c
drwxrwxrwx 1 root root       0 2008-01-12 18:05 RECYCLER
drwxrwxrwx 1 root root    4096 2008-01-12 18:05 System Volume Information

andreas@andreas-desktop:~$ cat /mnt/sda1/boot.ini /mnt/sdb1/boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
cat: /mnt/sdb1/boot.ini: No such file or directory

---

### Post by caljohnsmith on 2008-12-06
OK, your sda1 Windows partition does have the necessary boot files, and your boot.ini file looks like it is configured correctly; in order to get a better confirmation of which drive you are booting on start up, please post the output of:
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one. I think the next step would be to use "testdisk" to fix any problems with the file system parameters being corrupt in your Windows partition boot sector. To do that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows from Grub.

---

### Post by anil7 on 2008-12-06
It worked!!!!!!!!!!! Thank u so much!!! You are my hero!! I am so excited!

---

### Post by caljohnsmith on 2008-12-06
Glad to hear testdisk fixed the problem; cheers and have fun with your OSes. :)

---

