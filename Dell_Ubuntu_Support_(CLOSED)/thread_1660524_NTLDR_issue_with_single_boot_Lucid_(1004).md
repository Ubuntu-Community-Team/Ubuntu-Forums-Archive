---
title: "NTLDR issue with single boot Lucid (10/04)"
date: 2011-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ammortiser on 2011-01-05
Hello,

 Having been using my Dell Inspiron 1720 laptop in dual boot mode for some time I found that I wasn't using Vista at all and so I decided to opt for a single boot machine with only Kubuntu Lucid (10/04) installed and went through the usual installation procedure using "entire disk". I now have a machine that won't boot into its new OS due to an NTLDR is missing statement each time I try to boot.

 The installation appears to have gone as planned and I can't see anything in the BIOS that would explain matters.

 Any ideas or suggestions would be most welcome as I seem to have a dead machine until I can sort this out.

 Thanks in anticipation of your kind replies.

---

### Post by anystupidname1 on 2011-01-05
You need to install Grub to the boot record. Either you picked a wrong option during the install or something went wonky. Not to worry, boot back to that install CD (but don't reinstall):

```
sudo fdisk -l
sudo mount /dev/sda<?> /mnt
sudo mount --bind /dev /mnt/dev/
sudo chroot /mnt
sudo grub-mkconfig
grub-install /dev/sda
```

NOTE: in the first step, you need to identify your disk as it could be something other than /dev/sda which is why the <?> is there

---

### Post by ammortiser on 2011-01-05
Thanks for your reply. I did as you said but had problems...see copy of terminal report:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003cfe2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37785   303502336   83  Linux
/dev/sda2           37785       38914     9066497    5  Extended
/dev/sda5           37785       38914     9066496   82  Linux swap / Solaris

Disk /dev/sdb: 1060 MB, 1060371968 bytes
64 heads, 32 sectors/track, 1011 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1012     1035503+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 63, 32) logical=(1011, 15, 31)

Disk /dev/sdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf266f18a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15017   120624021    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev/
mount: mount point /mnt/dev/ does not exist

 There seems to be some issue with mount. Any ideas?

 Thanks again for your help.

---

### Post by drs305 on 2011-01-05
It appears that your Ubuntu installation is on sda1. You can install Grub2 to the MBR from the LiveCd without chrooting, although you can't update grub until you reboot.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Don't use the partition number in the second command.

These commands should point the sda MBR to look at sda1, where your Grub2 files reside. Make sure on reboot that your BIOS boots from the Ubuntu drive first (sda).

If booting still fails, please download and run the boot info script and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by ammortiser on 2011-01-05
Thank you! The results of that check showed that all appeared to be well and once I followed your advice and modified the boot order of my drives in the BIOS (I had had USB first (installing via a flash drive prepared with unetbootin) and my internal HD second) boot worked as it should again.

 My compliments on your support forum...I'm support staff on the SMF Forums system and am all too well aware of how hard it is to give such good support and advice.

 Once more Thank You!

---

