---
title: "BIOS can't see hard drive"
date: 2015-05-27
forum: Fedora/RedHat and derivatives
---

### Post by jman88888 on 2015-05-27
I am dual-booting win7 and linux and I can't get to either one right now.  When I go into the BIOS all that it will let me select for boot options is the cd-rom and a flash drive (if one is inserted).  Grub is installed on sda7 which is my linux partition.  Sda1 is an EFI partition, Sda3 is win7, sda4 is ntfs storage, and sda5 is a windows recovery partition, sda6 is a BIOS boot partition.  I'm using an Asus U47VC laptop.  UEFI boot is enabled.  Tried boot-repair-disk but that didn't fix it.  Any ideas on how to get my BIOS to boot from sda7?

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792   586,731,519   586,057,728 Data partition (Windows/Linux)
/dev/sda4     586,731,520 1,315,066,691   728,335,172 Data partition (Windows/Linux)
/dev/sda5   1,412,718,592 1,465,147,391    52,428,800 Windows Recovery Environment (Windows)
/dev/sda6   1,315,067,904 1,315,069,951         2,048 BIOS Boot partition
/dev/sda7   1,315,069,952 1,396,174,847    81,104,896 Data partition (Windows/Linux)
/dev/sda8   1,396,174,848 1,412,718,591    16,543,744 Swap partition (Linux)

---

### Post by oldfred on 2015-05-27
It is not really BIOS if you are booting in UEFI mode. UEFI has replaced BIOS but has a compatibility mode CSM.
Do you still have UEFI on, not the CSM/BIOS?

Post link to summary report from Boot-Repair.

---

### Post by jman88888 on 2015-05-28
Thank's for the reply.  Yes, it's still turned on.  I didn't see anything about compatibility mode.

[http://paste.ubuntu.com/11362572/](http://paste.ubuntu.com/11362572/)

---

### Post by oldfred on 2015-05-28
Is this only Centos now?

I do not know if Boot-Repair fully works with Centos or not. It expects certain applications to run and does work on all Debian based. 
It seemed to have some issue adding an efi boot entry with efibootmgr.

You do show grub in MBR for a BIOS boot. Is that just an old entry or did you install in CSM/BIOS mode?

You could try the copy of grub or shim(?) to /EFI/Boot/bootx64.efi and add that to UEFI.

 sudo efibootmgr -c -L "Hard drive" -l "\EFI\Boot\bootx64.efi"
sudo efibootmgr -v


 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by howefield on 2015-05-28
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by jman88888 on 2015-05-30
Tried reading through the links.  For the first link it doesn't do me any good because when I try and get to the EFI boot prompt it says not found.  I'm definitely still in EFI mode.  I will attach a couple of pictures of my BIOS.  Here's the output from those commands.  I tried booting after running them but the BIOS still doesn't show the hard drive in the boot options and it boots from the USB drive (EFI Sandisk).

```
lubuntu@lubuntu:~$ sudo efibootmgr 
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0002,0004
Boot0002* Hard Drive 
Boot0004* CD/DVD Drive 
Boot0005* UEFI: SanDisk Cruzer 8.02
lubuntu@lubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0002,0004
Boot0002* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.S.a.n.D.i.s.k. .C.r.u.z.e.r. .8...0.2....................A.............................<..Gd-.;.A..MQ..L.S.a.n.D.i.s.k. .C.r.u.z.e.r. .8...0.2......AMBO
Boot0004* CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.H.L.-.D.T.-.S.T. .D.V.D.R.A.M. .G.U.6.0.N....................A...........................>..Gd-.;.A..MQ..L.X.K.C.F.7.4.0.0.1.1. .6. . . . . . . . ......AMBO
Boot0005* UEFI: SanDisk Cruzer 8.02    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(3,0)HD(1,2,3b9ffd,00000000)AMBO
lubuntu@lubuntu:~$ 
lubuntu@lubuntu:~$ sudo efibootmgr -c -L "Hard drive" -l "\EFI\Boot\bootx64.efi"
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0000,0005,0002,0004
Boot0002* Hard Drive 
Boot0004* CD/DVD Drive 
Boot0005* UEFI: SanDisk Cruzer 8.02
Boot0000* Hard drive
lubuntu@lubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0000,0005,0002,0004
Boot0000* Hard drive    HD(1,800,64000,888f9ea7-33b6-4cdc-b1e7-b91656ba023e)File(\EFI\Boot\bootx64.efi)
Boot0002* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.S.a.n.D.i.s.k. .C.r.u.z.e.r. .8...0.2....................A.............................<..Gd-.;.A..MQ..L.S.a.n.D.i.s.k. .C.r.u.z.e.r. .8...0.2......AMBO
Boot0004* CD/DVD Drive     BIOS(3,0,00)AMGOAMNO........o.H.L.-.D.T.-.S.T. .D.V.D.R.A.M. .G.U.6.0.N....................A...........................>..Gd-.;.A..MQ..L.X.K.C.F.7.4.0.0.1.1. .6. . . . . . . . ......AMBO
Boot0005* UEFI: SanDisk Cruzer 8.02    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(3,0)HD(1,2,3b9ffd,00000000)AMBO
lubuntu@lubuntu:~$ 


```

---

### Post by oldfred on 2015-05-30
You added an efi boot entry for bootx64.efi.
Did you copy grub or shim into /EFI/Boot/bootx64.efi. or renamed after copy.

EFI\Boot\bootx64.efi

---

### Post by jman88888 on 2015-05-30
I went into /EFI/centos and copied grubx64.efi into /EFI/Boot and renamed it bootx64.efi.  Then I ran those commands but still the hard drive doesn't show up under boot options and it boots from USB.  In the BIOS it has an option to add a new boot option and you can point it to an .efi file.  I want to point it to this .efi file but I can't figure out exactly what to type as the boot option.  I attached screenshots in an earlier post that show this and they have an example path in the top right corner but I can't figure out exactly what I would type to point it to the .efi file on my hard drive.

---

### Post by oldfred on 2015-05-30
You show these two entries, first looks like the UEFI entry you added. The second may just be a default BIOS boot entry.

```
Boot0000* Hard drive    HD(1,800,64000,888f9ea7-33b6-4cdc-b1e7-b91656ba023e)[COLOR=#ff0000]File(\EFI\Boot\bootx64.efi[/COLOR])
Boot0002* Hard Drive     BIOS(2,0,00)AMGOAMNO........o.S.a.n.D.i.s.k. .C.r.u.z.e.r. .8...0.2..............
```

---

### Post by jman88888 on 2015-05-30
The sandisk is my usb drive with boot-repair on it which is what I've been booting from.  Under add new boot option the example filename they give is  fs0:\path\filename.efi.  So if I'm guessing I need to add "hd0:\EFI\Boot\bootx64.efi" as an option?

---

### Post by jman88888 on 2015-05-30
well that doesn't work.  Would installing Kubuntu 15.04  and then running boot-repair-disk fix this problem?

---

### Post by jman88888 on 2015-05-30
That didn't work.  It still refuses to see the hard drive as a boot option.  I did notice one thing when I was installing kubuntu, there is a 1MB partition called biosgrub which is sda5.  The folder /EFI/boot contains a bootx64.efi file.  I think this may be the source of all of my problems but I'm not sure what to do with it.  Here's the ls -l:
```
lubuntu@lubuntu:/mnt$ ls -l
total 13202891
-rwxrwxrwx 1 root root    2243072 May  4  2012 AsChange.exe
-rwxrwxrwx 1 root root         57 Jun 20  2012 AsConfig.ini
-rwxrwxrwx 1 root root    2264528 Nov 30  2011 AsDeploy.exe
-rwxrwxrwx 1 root root      20478 Jun 20  2012 AsDeploy.log
-rwxrwxrwx 2 root root        577 May 19  2012 AsDiskpart.log
-rwxrwxrwx 1 root root      41941 Jun 20  2012 AsFac.log
-rwxrwxrwx 1 root root   27448843 Jun 19  2012 AsKit64.wim
-rwxrwxrwx 1 root root   27447975 Jun 19  2012 AsKit.wim
-rwxrwxrwx 2 root root        142 Jan  4  2012 AsPartition.log
-rwxrwxrwx 2 root root         34 May  4  2012 AsToolCDVer.txt
-rwxrwxrwx 1 root root 4069644937 Jun 19  2012 asus2.SWM
-rwxrwxrwx 1 root root 3610647792 Jun 19  2012 asus3.SWM
drwxrwxrwx 1 root root          0 Jun 20  2012 ASUSLog
-rwxrwxrwx 1 root root 4086882166 Jun 19  2012 asus.SWM
drwxrwxrwx 1 root root       4096 Nov 18  2011 boot
-rwxrwxrwx 1 root root     383562 Jul 14  2009 bootmgr
-rwxrwxrwx 1 root root     667712 Jul 14  2009 bootmgr.efi
-rwxrwxrwx 2 root root          0 Jun 20  2012 createiffs.txt
drwxrwxrwx 1 root root       4096 Nov 24  2011 DisableS3S4
-rwxrwxrwx 1 root root 1691428807 Jun 19  2012 DRIVER64.wim
drwxrwxrwx 1 root root          0 Nov 18  2011 EFI
-rwxrwxrwx 1 root root     581008 Jul 13  2009 imagex.exe
drwxrwxrwx 1 root root          0 Aug  7  2013 Recovery
drwxrwxrwx 1 root root          0 Jun 20  2012 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 Jun 20  2012 sources
-rwxrwxrwx 2 root root       5879 Jul 13  2011 SWPackage.ini
-rwxrwxrwx 2 root root       4701 Sep  6  2011 SWPackage.ini.bak
-rwxrwxrwx 2 root root       5879 Jul 13  2011 SWPackageusb.ini
drwxrwxrwx 1 root root          0 Jun 19  2012 System Volume Information
drwxrwxrwx 1 root root          0 Nov 30  2011 Tools


```

---

### Post by oldfred on 2015-05-31
If you install grub in BIOS boot mode, it requires the bios_grub partition. That partition is not used if booting in UEFI mode. And if in BIOS mode the efi partition is not used.
Which version of grub then do you have installed? grub-pc(BIOS) or grub-efi-amd64(UEFI) 
Not sure if package names are exactly the same with your system.

Boot-Repair does convert an install from UEFI to BIOS or vice-versa, if you have correct partitions. But all it is doing is uninstalling one version of grub and installing the other using a chroot.

---

