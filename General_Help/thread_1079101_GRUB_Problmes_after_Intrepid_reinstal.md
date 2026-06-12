---
title: "GRUB Problmes after Intrepid reinstal"
date: 2009-02-24
forum: General Help
---

### Post by DavidMP on 2009-02-24
Hello,

I have been looking around for ways to solve this problem but so far I haven't been successful; I'm not sure what else to try so here it is.

I have been running Intrepid for a while (as a dual boot with XP) and it started giving problems so I decided to migrate \home to a new partition and reinstall Intrepid from the Live CD

Since I did this I get a GRUB Error 15 but I can see all my files and partitions when I boot on the Live CD. I have been able to boot back to WinXP through the "Super GRUB Disk" but using the repair tool for GRUB within SGD gives the same error 15. Trying to repair GRUB from the Live CD gives the same result.

```
sudo grub
find /boot/grub/stage1
```

returns

```
Error 15: File not found
```

Any idea about what files to copy and where to paste into? 
Does anybody have any idea as to how to force a complete reinstall of the GRUB loader since SGD doesn't do it? 
Any ideas about what else to try short of reformatting my linux partition and installing again?

Any ideas would be greatly appreciated

---

### Post by caljohnsmith on 2009-02-24
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by DavidMP on 2009-02-24
Thank you very much for the help and sorry for not replying earlier; the trouble is with my home computer and I was at work. Here is the output of the script.



```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9749a12

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   159,653,969   159,653,907   7 HPFS/NTFS
/dev/sda2         159,653,970   488,392,064   328,738,095   5 Extended
/dev/sda5         159,654,033   317,990,609   158,336,577  83 Linux
/dev/sda6         476,311,248   488,392,064    12,080,817  82 Linux swap / Solaris
/dev/sda7         317,990,673   476,311,184   158,320,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="619A9A16599F42D7" TYPE="ntfs" 
/dev/sda5: UUID="e0e417f5-309c-43d4-864f-5e21927b2857" TYPE="ext3" 
/dev/sda6: UUID="7cc40b26-35f4-4b0e-be7b-0dbdeccfbc18" TYPE="swap" 
/dev/sda7: UUID="8bb711c7-b046-43ef-a388-0b16836dce57" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e0e417f5-309c-43d4-864f-5e21927b2857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8bb711c7-b046-43ef-a388-0b16836dce57 /home           ext3    relatime        0       2
# /dev/sda1
UUID=619A9A16599F42D7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=7cc40b26-35f4-4b0e-be7b-0dbdeccfbc18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 130.6GB: boot/vmlinuz-2.6.27-7-generic
 130.6GB: vmlinuz
```

I do have a fully functional windows XP partition (but I can only get to it through the super grub disk) and the data in sda5 and sda7 is accessible through the live CD.

Thanks

David

---

### Post by caljohnsmith on 2009-02-25
It looks like the Ubuntu installer did not install Grub, nor did it completely install Ubuntu's boot files; Ubuntu is missing its /boot/initrd.img-2.6.27-7-generic file. Did you get any errors when you installed Ubuntu? Did it say it completed successfully at the end? I would recommend first running the "check CD for defects" option from the main menu of the Live CD, and if that doesn't show anything wrong, I think I would download another Ubuntu Live CD ISO, check the MD5 sum, burn it to CD at slow speed (4X), run "check CD for defects" on it, and if it passes, try reinstalling Ubuntu. Let me know how that goes or if you run into problems.

---

### Post by DavidMP on 2009-02-25
Thanks 
It did say install was OK. And I checked the Live CD and it said it was OK. I also did a memtest and the computer was also OK. I don't think I did a checksum.
I'm downloading another image to burn and check (that'll be tomorrow, it says it will take 8h to download)

Cheers

David

---

### Post by DavidMP on 2009-02-27
So I burnt a newly downloaded image. The disk check and checksum are OK. I installed again defining sda5 as \ and sda7 as \home. At the end it said that the program had ended in an unexpected manner and I still have the same error 15 at the grub 1.5 stage upon reboot.

Any other ideas are very welcome.

Thanks

David

P.S. Here is the boot information

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9749a12

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   159,653,969   159,653,907   7 HPFS/NTFS
/dev/sda2         159,653,970   488,392,064   328,738,095   5 Extended
/dev/sda5         159,654,033   317,990,609   158,336,577  83 Linux
/dev/sda6         476,311,248   488,392,064    12,080,817  82 Linux swap / Solaris
/dev/sda7         317,990,673   476,311,184   158,320,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="619A9A16599F42D7" TYPE="ntfs" 
/dev/sda5: UUID="43a7cb5f-2b59-41cb-8c90-a834663c615d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7cc40b26-35f4-4b0e-be7b-0dbdeccfbc18" TYPE="swap" 
/dev/sda7: UUID="8bb711c7-b046-43ef-a388-0b16836dce57" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=43a7cb5f-2b59-41cb-8c90-a834663c615d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8bb711c7-b046-43ef-a388-0b16836dce57 /home           ext3    relatime        0       2
# /dev/sda1
UUID=619A9A16599F42D7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=7cc40b26-35f4-4b0e-be7b-0dbdeccfbc18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  83.2GB: boot/vmlinuz-2.6.27-7-generic
  83.2GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-02-27
> **DavidMP said:**
> At the end it said that the program had ended in an unexpected manner and I still have the same error 15 at the grub 1.5 stage upon reboot.
According to the script, the exact same thing happened again; you are missing at least Grub and your /boot/initrd.img-2.6.27-7-generic file. What exactly was the error you received? Did the installer give you any more information than just saying it quit in an unexpected manner? It looks like that error is the crux of the problem.

---

### Post by DavidMP on 2009-02-27
The crash is in "ubiquity" and it gave me this report

```
The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

libgcc1, libxml2, initramfs-tools, udev, libsqlite3-0, libssl0.9.8, procps, sudo, console-setup, libpam-modules, passwd, xkb-data, libstdc++6, libpam-runtime, libc6, libpam0g, busybox-initramfs, perl-base, libvolume-id0, dpkg, gcc-4.3-base
```

I'm upgrading them now...

They upgraded OK but I still have GRUB error 15 upon reboot.

I reinstalled and I still have the crash at the end except this time it gives me a different error. Here is the apport information.

```
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 437, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 825, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2112, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 373, in run
    self.configure_user()
  File "/usr/share/ubiquity/install.py", line 1265, in configure_user
    raise InstallStepError("UserSetupApply failed with code %d" % ret)
InstallStepError: UserSetupApply failed with code 1

00400000-00525000 r-xp 00000000 00:12 352                                /usr/bin/python2.5
00724000-00725000 r--p 00124000 00:12 352                                /usr/bin/python2.5
00725000-00757000 rw-p 00125000 00:12 352                                /usr/bin/python2.5
00757000-0075f000 rw-p 00757000 00:00 0 
01e15000-03b82000 rw-p 01e15000 00:00 0                                  [heap]
7f693409e000-7f69340b4000 r-xp 00000000 00:12 2045                       /lib/libgcc_s.so.1
7f69340b4000-7f69342b4000 ---p 00016000 00:12 2045                       /lib/libgcc_s.so.1
7f69342b4000-7f69342b5000 r--p 00016000 00:12 2045                       /lib/libgcc_s.so.1
7f69342b5000-7f69342b6000 rw-p 00017000 00:12 2045                       /lib/libgcc_s.so.1
7f69342b6000-7f69343a7000 r-xp 00000000 00:12 2044                       /usr/lib/libstdc++.so.6.0.10
7f69343a7000-7f69345a7000 ---p 000f1000 00:12 2044                       /usr/lib/libstdc++.so.6.0.10
7f69345a7000-7f69345ae000 r--p 000f1000 00:12 2044                       /usr/lib/libstdc++.so.6.0.10
7f69345ae000-7f69345b0000 rw-p 000f8000 00:12 2044                       /usr/lib/libstdc++.so.6.0.10
7f69345b0000-7f69345c3000 rw-p 7f69345b0000 00:00 0 
7f69345c3000-7f693467e000 r-xp 00000000 00:12 2042                       /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
7f693467e000-7f693487e000 ---p 000bb000 00:12 2042                       /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
7f693487e000-7f6934881000 r--p 000bb000 00:12 2042                       /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
7f6934881000-7f6934882000 rw-p 000be000 00:12 2042                       /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
7f6934882000-7f69348a3000 r-xp 00000000 00:12 398                        /usr/lib/python2.5/site-packages/apt_pkg.so
7f69348a3000-7f6934aa2000 ---p 00021000 00:12 398                        /usr/lib/python2.5/site-packages/apt_pkg.so
7f6934aa2000-7f6934aa3000 r--p 00020000 00:12 398                        /usr/lib/python2.5/site-packages/apt_pkg.so
7f6934aa3000-7f6934aa8000 rw-p 00021000 00:12 398                        /usr/lib/python2.5/site-packages/apt_pkg.so
7f6934aa8000-7f6934aaa000 r-xp 00000000 00:12 21926                      /usr/lib/python2.5/lib-dynload/grp.so
7f6934aaa000-7f6934ca9000 ---p 00002000 00:12 21926                      /usr/lib/python2.5/lib-dynload/grp.so
7f6934ca9000-7f6934caa000 r--p 00001000 00:12 21926                      /usr/lib/python2.5/lib-dynload/grp.so
7f6934caa000-7f6934cab000 rw-p 00002000 00:12 21926                      /usr/lib/python2.5/lib-dynload/grp.so
7f6934cab000-7f6934cae000 r-xp 00000000 00:12 486                        /usr/lib/python2.5/lib-dynload/_random.so
7f6934cae000-7f6934ead000 ---p 00003000 00:12 486                        /usr/lib/python2.5/lib-dynload/_random.so
7f6934ead000-7f6934eae000 r--p 00002000 00:12 486                        /usr/lib/python2.5/lib-dynload/_random.so
7f6934eae000-7f6934eaf000 rw-p 00003000 00:12 486                        /usr/lib/python2.5/lib-dynload/_random.so
7f6934eaf000-7f6934ebe000 r-xp 00000000 00:12 9004                       /lib/libbz2.so.1.0.4
7f6934ebe000-7f69350be000 ---p 0000f000 00:12 9004                       /lib/libbz2.so.1.0.4
7f69350be000-7f69350bf000 r--p 0000f000 00:12 9004                       /lib/libbz2.so.1.0.4
7f69350bf000-7f69350c0000 rw-p 00010000 00:12 9004                       /lib/libbz2.so.1.0.4
7f69350c0000-7f69350f6000 r-xp 00000000 00:12 17441                      /usr/lib/libcroco-0.6.so.3.0.1
7f69350f6000-7f69352f5000 ---p 00036000 00:12 17441                      /usr/lib/libcroco-0.6.so.3.0.1
7f69352f5000-7f69352f9000 rw-p 00035000 00:12 17441                      /usr/lib/libcroco-0.6.so.3.0.1
7f69352f9000-7f693532f000 r-xp 00000000 00:12 17438                      /usr/lib/libgsf-1.so.114.0.8
7f693532f000-7f693552e000 ---p 00036000 00:12 17438                      /usr/lib/libgsf-1.so.114.0.8
7f693552e000-7f6935531000 r--p 00035000 00:12 17438                      /usr/lib/libgsf-1.so.114.0.8
7f6935531000-7f6935532000 rw-p 00038000 00:12 17438                      /usr/lib/libgsf-1.so.114.0.8
7f6935532000-7f6935533000 rw-p 7f6935532000 00:00 0 
7f6935533000-7f6935536000 r--p 00000000 00:12 23157                      /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
7f6935536000-7f6935575000 r--p 00000000 00:12 1000                       /usr/lib/locale/en_CA.utf8/LC_CTYPE
7f6935575000-7f6935656000 r--p 00000000 00:12 22939                      /usr/lib/locale/en_CA.utf8/LC_COLLATE
7f6935656000-7f6935684000 r--p 00000000 00:12 22922                      /usr/share/fonts/truetype/ttf-indic-fonts-core/MuktiNarrow.ttf
7f6935684000-7f6935687000 r-xp 00000000 00:12 22921                      /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
7f6935687000-7f6935886000 ---p 00003000 00:12 22921                      /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
7f6935886000-7f6935887000 r--p 00002000 00:12 22921                      /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
7f6935887000-7f6935888000 rw-p 00003000 00:12 22921                      /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
7f6935888000-7f693588f000 r-xp 00000000 00:12 22919                      /usr/lib/pango/1.6.0/modules/pango-indic-fc.so
7f693588f000-7f6935a8f000 ---p 00007000 00:12 22919                      /usr/lib/pango/1.6.0/modules/pango-indic-fc.so
7f6935a8f000-7f6935a90000 r--p 00007000 00:12 22919                      /usr/lib/pango/1.6.0/modules/pango-indic-fc.so
7f6935a90000-7f6935a91000 rw-p 00008000 00:12 22919                      /usr/lib/pango/1.6.0/modules/pango-indic-fc.so
7f6935a91000-7f6935a93000 r-xp 00000000 00:12 22918                      /usr/lib/pango/1.6.0/modules/pango-indic-lang.so
7f6935a93000-7f6935c92000 ---p 00002000 00:12 22918                      /usr/lib/pango/1.6.0/modules/pango-indic-lang.so
7f6935c92000-7f6935c93000 r--p 00001000 00:12 22918                      /usr/lib/pango/1.6.0/modules/pango-indic-lang.so
7f6935c93000-7f6935c94000 rw-p 00002000 00:12 22918                      /usr/lib/pango/1.6.0/modules/pango-indic-lang.so
7f6935c94000-7f6935c98000 r-xp 00000000 00:12 21941                      /usr/lib/python2.5/lib-dynload/zlib.so
7f6935c98000-7f6935e97000 ---p 00004000 00:12 21941                      /usr/lib/python2.5/lib-dynload/zlib.so
7f6935e97000-7f6935e98000 r--p 00003000 00:12 21941                      /usr/lib/python2.5/lib-dynload/zlib.so
7f6935e98000-7f6935e9a000 rw-p 00004000 00:12 21941                      /usr/lib/python2.5/lib-dynload/zlib.so
7f6935e9a000-7f6935efa000 rw-s 00000000 00:09 524303                     /SYSV00000000 (deleted)
7f693608a000-7f69360bf000 r-xp 00000000 00:12 17353                      /usr/lib/librsvg-2.so.2.22.3
7f69360bf000-7f69362be000 ---p 00035000 00:12 17353                      /usr/lib/librsvg-2.so.2.22.3
7f69362be000-7f69362bf000 r--p 00034000 00:12 17353                      /usr/lib/librsvg-2.so.2.22.3
7f69362bf000-7f69362c0000 rw-p 00035000 00:12 17353                      /usr/lib/librsvg-2.so.2.22.3
7f69362c0000-7f69362c2000 r-xp 00000000 00:12 20955                      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f69362c2000-7f69364c1000 ---p 00002000 00:12 20955                      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f69364c1000-7f69364c2000 r--p 00001000 00:12 20955                      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f69364c2000-7f69364c3000 rw-p 00002000 00:12 20955                      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f69364c3000-7f69364f8000 r-xp 00000000 00:12 1933                       /usr/lib/python2.5/lib-dynload/pyexpat.so
7f69364f8000-7f69366f7000 ---p 00035000 00:12 1933                       /usr/lib/python2.5/lib-dynload/pyexpat.so
7f69366f7000-7f69366fa000 r--p 00034000 00:12 1933                       /usr/lib/python2.5/lib-dynload/pyexpat.so
7f69366fa000-7f69366fc000 rw-p 00037000 00:12 1933                       /usr/lib/python2.5/lib-dynload/pyexpat.so
7f69366fc000-7f6936cfd000 rw-p 7f69366fc000 00:00 0 
7f6936cfd000-7f6936d1f000 r-xp 00000000 00:12 19408                      /usr/lib/libjpeg.so.62.0.0
7f6936d1f000-7f6936f1f000 ---p 00022000 00:12 19408                      /usr/lib/libjpeg.so.62.0.0
7f6936f1f000-7f6936f20000 rw-p 00022000 00:12 19408                      /usr/lib/libjpeg.so.62.0.0
7f6936f20000-7f6936f24000 r-xp 00000000 00:12 21011                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f6936f24000-7f6937124000 ---p 00004000 00:12 21011                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f6937124000-7f6937125000 r--p 00004000 00:12 21011                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f6937125000-7f6937126000 rw-p 00005000 00:12 21011                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f6937126000-7f69371af000 r--p 00000000 00:12 21010                      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f69371af000-7f69371b1000 r-xp 00000000 00:12 17836                      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f69371b1000-7f69373b0000 ---p 00002000 00:12 17836                      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f69373b0000-7f69373b1000 r--p 00001000 00:12 17836                      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f69373b1000-7f69373b2000 rw-p 00002000 00:12 17836                      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f69373b2000-7f6937447000 r--p 00000000 00:12 17800                      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f6937447000-7f693744b000 r-xp 00000000 00:12 17093                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f693744b000-7f693764b000 ---p 00004000 00:12 17093                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f693764b000-7f693764c000 r--p 00004000 00:12 17093                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f693764c000-7f693764d000 rw-p 00005000 00:12 17093                      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f693764d000-7f693766e000 r-xp 00000000 00:12 17115                      /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7f693766e000-7f693786d000 ---p 00021000 00:12 17115                      /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7f693786d000-7f693786e000 r--p 00020000 00:12 17115                      /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7f693786e000-7f693786f000 rw-p 00021000 00:12 17115                      /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7f693786f000-7f6937878000 r-xp 00000000 00:12 22453                      /usr/lib/ubiquity/ubiquity/emap.so
7f6937878000-7f6937a78000 ---p 00009000 00:12 22453                      /usr/lib/ubiquity/ubiquity/emap.so
7f6937a78000-7f6937a79000 r--p 00009000 00:12 22453                      /usr/lib/ubiquity/ubiquity/emap.so
7f6937a79000-7f6937a7a000 rw-p 0000a000 00:12 22453                      /usr/lib/ubiquity/ubiquity/emap.so
7f6937a7a000-7f6937bcd000 r-xp 00000000 00:12 514                        /usr/lib/libxml2.so.2.6.32
7f6937bcd000-7f6937dcc000 ---p 00153000 00:12 514                        /usr/lib/libxml2.so.2.6.32
7f6937dcc000-7f6937dd4000 r--p 00152000 00:12 514                        /usr/lib/libxml2.so.2.6.32
7f6937dd4000-7f6937dd6000 rw-p 0015a000 00:12 514                        /usr/lib/libxml2.so.2.6.32
7f6937dd6000-7f6937dd7000 rw-p 7f6937dd6000 00:00 0 
7f6937dd7000-7f6937def000 r-xp 00000000 00:12 8831                       /usr/lib/libglade-2.0.so.0.0.7
7f6937def000-7f6937fee000 ---p 00018000 00:12 8831                       /usr/lib/libglade-2.0.so.0.0.7
7f6937fee000-7f6937fef000 r--p 00017000 00:12 8831                       /usr/lib/libglade-2.0.so.0.0.7
7f6937fef000-7f6937ff0000 rw-p 00018000 00:12 8831                       /usr/lib/libglade-2.0.so.0.0.7
7f6937ff0000-7f6937ff5000 r-xp 00000000 00:12 22407                      /usr/lib/python-support/python-glade2/python2.5/gtk-2.0/gtk/glade.so
7f6937ff5000-7f69381f4000 ---p 00005000 00:12 22407                      /usr/lib/python-support/python-glade2/python2.5/gtk-2.0/gtk/glade.so
7f69381f4000-7f69381f5000 r--p 00004000 00:12 22407                      /usr/lib/python-support/python-glade2/python2.5/gtk-2.0/gtk/glade.so
7f69381f5000-7f69381f6000 rw-p 00005000 00:12 22407                      /usr/lib/python-support/python-glade2/python2.5/gtk-2.0/gtk/glade.so
7f69381f6000-7f6938201000 r-xp 00000000 00:12 168                        /lib/libnss_files-2.8.90.so
7f6938201000-7f6938400000 ---p 0000b000 00:12 168                        /lib/libnss_files-2.8.90.so
7f6938400000-7f6938401000 r--p 0000a000 00:12 168                        /lib/libnss_files-2.8.90.so
7f6938401000-7f6938402000 rw-p 0000b000 00:12 168                        /lib/libnss_files-2.8.90.so
7f6938402000-7f693840c000 r-xp 00000000 00:12 166                        /lib/libnss_nis-2.8.90.so
7f693840c000-7f693860b000 ---p 0000a000 00:12 166                        /lib/libnss_nis-2.8.90.so
7f693860b000-7f693860c000 r--p 00009000 00:12 166                        /lib/libnss_nis-2.8.90.so
7f693860c000-7f693860d000 rw-p 0000a000 00:12 166                        /lib/libnss_nis-2.8.90.so
7f693860d000-7f6938623000 r-xp 00000000 00:12 164                        /lib/libnsl-2.8.90.so
7f6938623000-7f6938822000 ---p 00016000 00:12 164                        /lib/libnsl-2.8.90.so
7f6938822000-7f6938823000 r--p 00015000 00:12 164                        /lib/libnsl-2.8.90.so
7f6938823000-7f6938824000 rw-p 00016000 00:12 164                        /lib/libnsl-2.8.90.so
7f6938824000-7f6938826000 rw-p 7f6938824000 00:00 0 
7f6938826000-7f693882e000 r-xp 00000000 00:12 162                        /lib/libnss_compat-2.8.90.so
7f693882e000-7f6938a2d000 ---p 00008000 00:12 162                        /lib/libnss_compat-2.8.90.so
7f6938a2d000-7f6938a2e000 r--p 00007000 00:12 162                        /lib/libnss_compat-2.8.90.so
7f6938a2e000-7f6938a2f000 rw-p 00008000 00:12 162                        /lib/libnss_compat-2.8.90.so
7f6938a2f000-7f6938b10000 r--p 00000000 00:12 997                        /usr/lib/locale/en_US.utf8/LC_COLLATE
7f6938b10000-7f6938b14000 r-xp 00000000 00:12 20985                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pangocairo.so
7f6938b14000-7f6938d13000 ---p 00004000 00:12 20985                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pangocairo.so
7f6938d13000-7f6938d14000 r--p 00003000 00:12 20985                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pangocairo.so
7f6938d14000-7f6938d15000 rw-p 00004000 00:12 20985                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pangocairo.so
7f6938d15000-7f6938d52000 r-xp 00000000 00:12 20976                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/atk.so
7f6938d52000-7f6938f52000 ---p 0003d000 00:12 20976                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/atk.so
7f6938f52000-7f6938f55000 r--p 0003d000 00:12 20976                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/atk.so
7f6938f55000-7f6938f5a000 rw-p 00040000 00:12 20976                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/atk.so
7f6938f5a000-7f6938f5e000 r-xp 00000000 00:12 20957                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/unix.so
7f6938f5e000-7f693915d000 ---p 00004000 00:12 20957                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/unix.so
7f693915d000-7f693915e000 r--p 00003000 00:12 20957                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/unix.so
7f693915e000-7f693915f000 rw-p 00004000 00:12 20957                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/unix.so
7f693915f000-7f6939192000 r-xp 00000000 00:12 20952                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/_gio.so
7f6939192000-7f6939391000 ---p 00033000 00:12 20952                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/_gio.so
7f6939391000-7f6939395000 r--p 00032000 00:12 20952                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/_gio.so
7f6939395000-7f693939b000 rw-p 00036000 00:12 20952                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gio/_gio.so
7f693939b000-7f69393ae000 r-xp 00000000 00:12 20935                      /usr/lib/python2.5/site-packages/cairo/_cairo.so
7f69393ae000-7f69395ad000 ---p 00013000 00:12 20935                      /usr/lib/python2.5/site-packages/cairo/_cairo.so
7f69395ad000-7f69395ae000 r--p 00012000 00:12 20935                      /usr/lib/python2.5/site-packages/cairo/_cairo.so
7f69395ae000-7f69395b2000 rw-p 00013000 00:12 20935                      /usr/lib/python2.5/site-packages/cairo/_cairo.so
7f69395b2000-7f69395b7000 r-xp 00000000 00:12 7631                       /usr/lib/libXdmcp.so.6.0.0
7f69395b7000-7f69397b6000 ---p 00005000 00:12 7631                       /usr/lib/libXdmcp.so.6.0.0
7f69397b6000-7f69397b7000 rw-p 00004000 00:12 7631                       /usr/lib/libXdmcp.so.6.0.0
7f69397b7000-7f69397b9000 r-xp 00000000 00:12 7629                       /usr/lib/libXau.so.6.0.0
7f69397b9000-7f69399b8000 ---p 00002000 00:12 7629                       /usr/lib/libXau.so.6.0.0
7f69399b8000-7f69399b9000 rw-p 00001000 00:12 7629                       /usr/lib/libXau.so.6.0.0
7f69399b9000-7f69399ba000 r-xp 00000000 00:12 7625                       /usr/lib/libxcb-xlib.so.0.0.0
7f69399ba000-7f6939bb9000 ---p 00001000 00:12 7625                       /usr/lib/libxcb-xlib.so.0.0.0
7f6939bb9000-7f6939bba000 r--p 00000000 00:12 7625                       /usr/lib/libxcb-xlib.so.0.0.0
7f6939bba000-7f6939bbb000 rw-p 00001000 00:12 7625                       /usr/lib/libxcb-xlib.so.0.0.0
7f6939bbb000-7f6939be2000 r-xp 00000000 00:12 8032                       /usr/lib/libexpat.so.1.5.2
7f6939be2000-7f6939de2000 ---p 00027000 00:12 8032                       /usr/lib/libexpat.so.1.5.2
7f6939de2000-7f6939de4000 r--p 00027000 00:12 8032                       /usr/lib/libexpat.so.1.5.2
7f6939de4000-7f6939de5000 rw-p 00029000 00:12 8032                       /usr/lib/libexpat.so.1.5.2
7f6939de5000-7f6939e00000 r-xp 00000000 00:12 7627                       /usr/lib/libxcb.so.1.0.0
7f6939e00000-7f6939fff000 ---p 0001b000 00:12 7627                       /usr/lib/libxcb.so.1.0.0
7f6939fff000-7f693a000000 r--p 0001a000 00:12 7627                       /usr/lib/libxcb.so.1.0.0
7f693a000000-7f693a001000 rw-p 0001b000 00:12 7627                       /usr/lib/libxcb.so.1.0.0
7f693a001000-7f693a008000 r-xp 00000000 00:12 8486                       /usr/lib/libxcb-render.so.0.0.0
7f693a008000-7f693a208000 ---p 00007000 00:12 8486                       /usr/lib/libxcb-render.so.0.0.0
7f693a208000-7f693a209000 r--p 00007000 00:12 8486                       /usr/lib/libxcb-render.so.0.0.0
7f693a209000-7f693a20a000 rw-p 00008000 00:12 8486                       /usr/lib/libxcb-render.so.0.0.0
7f693a20a000-7f693a20d000 r-xp 00000000 00:12 8484                       /usr/lib/libxcb-render-util.so.0.0.0
7f693a20d000-7f693a40c000 ---p 00003000 00:12 8484                       /usr/lib/libxcb-render-util.so.0.0.0
7f693a40c000-7f693a40d000 r--p 00002000 00:12 8484                       /usr/lib/libxcb-render-util.so.0.0.0
7f693a40d000-7f693a40e000 rw-p 00003000 00:12 8484                       /usr/lib/libxcb-render-util.so.0.0.0
7f693a40e000-7f693a433000 r-xp 00000000 00:12 8481                       /usr/lib/libpng12.so.0.27.0
7f693a433000-7f693a633000 ---p 00025000 00:12 8481                       /usr/lib/libpng12.so.0.27.0
7f693a633000-7f693a635000 rw-p 00025000 00:12 8481                       /usr/lib/libpng12.so.0.27.0
7f693a635000-7f693a677000 r-xp 00000000 00:12 8475                       /usr/lib/libpixman-1.so.0.12.0
7f693a677000-7f693a876000 ---p 00042000 00:12 8475                       /usr/lib/libpixman-1.so.0.12.0
7f693a876000-7f693a878000 r--p 00041000 00:12 8475                       /usr/lib/libpixman-1.so.0.12.0
7f693a878000-7f693a879000 rw-p 00043000 00:12 8475                       /usr/lib/libpixman-1.so.0.12.0
7f693a879000-7f693a893000 r-xp 00000000 00:12 226                        /lib/libselinux.so.1
7f693a893000-7f693aa92000 ---p 0001a000 00:12 226                        /lib/libselinux.so.1
7f693aa92000-7f693aa93000 r--p 00019000 00:12 226                        /lib/libselinux.so.1
7f693aa93000-7f693aa94000 rw-p 0001a000 00:12 226                        /lib/libselinux.so.1
7f693aa94000-7f693aa95000 rw-p 7f693aa94000 00:00 0 
7f693aa95000-7f693aa9e000 r-xp 00000000 00:12 8507                       /usr/lib/libXcursor.so.1.0.2
7f693aa9e000-7f693ac9e000 ---p 00009000 00:12 8507                       /usr/lib/libXcursor.so.1.0.2
7f693ac9e000-7f693ac9f000 rw-p 00009000 00:12 8507                       /usr/lib/libXcursor.so.1.0.2
7f693ac9f000-7f693aca6000 r-xp 00000000 00:12 8505                       /usr/lib/libXrandr.so.2.1.0
7f693aca6000-7f693aea5000 ---p 00007000 00:12 8505                       /usr/lib/libXrandr.so.2.1.0
7f693aea5000-7f693aea6000 r--p 00006000 00:12 8505                       /usr/lib/libXrandr.so.2.1.0
7f693aea6000-7f693aea7000 rw-p 00007000 00:12 8505                       /usr/lib/libXrandr.so.2.1.0
7f693aea7000-7f693aeb0000 r-xp 00000000 00:12 8503                       /usr/lib/libXi.so.6.0.0
7f693aeb0000-7f693b0b0000 ---p 00009000 00:12 8503                       /usr/lib/libXi.so.6.0.0
7f693b0b0000-7f693b0b1000 r--p 00009000 00:12 8503                       /usr/lib/libXi.so.6.0.0
7f693b0b1000-7f693b0b2000 rw-p 0000a000 00:12 8503                       /usr/lib/libXi.so.6.0.0
7f693b0b2000-7f693b0b4000 r-xp 00000000 00:12 8491                       /usr/lib/libXinerama.so.1.0.0
7f693b0b4000-7f693b2b3000 ---p 00002000 00:12 8491                       /usr/lib/libXinerama.so.1.0.0
7f693b2b3000-7f693b2b4000 rw-p 00001000 00:12 8491                       /usr/lib/libXinerama.so.1.0.0
7f693b2b4000-7f693b2bd000 r-xp 00000000 00:12 8488                       /usr/lib/libXrender.so.1.3.0
7f693b2bd000-7f693b4bc000 ---p 00009000 00:12 8488                       /usr/lib/libXrender.so.1.3.0
7f693b4bc000-7f693b4bd000 r--p 00008000 00:12 8488                       /usr/lib/libXrender.so.1.3.0
7f693b4bd000-7f693b4be000 rw-p 00009000 00:12 8488                       /usr/lib/libXrender.so.1.3.0
7f693b4be000-7f693b4ce000 r-xp 00000000 00:12 8495                       /usr/lib/libXext.so.6.4.0
7f693b4ce000-7f693b6ce000 ---p 00010000 00:12 8495                       /usr/lib/libXext.so.6.4.0
7f693b6ce000-7f693b6d0000 rw-p 00010000 00:12 8495                       /usr/lib/libXext.so.6.4.0
7f693b6d0000-7f693b6d5000 r-xp 00000000 00:12 8501                       /usr/lib/libXfixes.so.3.1.0
7f693b6d5000-7f693b8d4000 ---p 00005000 00:12 8501                       /usr/lib/libXfixes.so.3.1.0
7f693b8d4000-7f693b8d5000 rw-p 00004000 00:12 8501                       /usr/lib/libXfixes.so.3.1.0
7f693b8d5000-7f693b8d7000 r-xp 00000000 00:12 8499                       /usr/lib/libXdamage.so.1.1.0
7f693b8d7000-7f693bad6000 ---p 00002000 00:12 8499                       /usr/lib/libXdamage.so.1.1.0
7f693bad6000-7f693bad7000 rw-p 00001000 00:12 8499                       /usr/lib/libXdamage.so.1.1.0
7f693bad7000-7f693bad9000 r-xp 00000000 00:12 8497                       /usr/lib/libXcomposite.so.1.0.0
7f693bad9000-7f693bcd8000 ---p 00002000 00:12 8497                       /usr/lib/libXcomposite.so.1.0.0
7f693bcd8000-7f693bcd9000 r--p 00001000 00:12 8497                       /usr/lib/libXcomposite.so.1.0.0
7f693bcd9000-7f693bcda000 rw-p 00002000 00:12 8497                       /usr/lib/libXcomposite.so.1.0.0
7f693bcda000-7f693bddd000 r-xp 00000000 00:12 7621                       /usr/lib/libX11.so.6.2.0
7f693bddd000-7f693bfdd000 ---p 00103000 00:12 7621                       /usr/lib/libX11.so.6.2.0
7f693bfdd000-7f693bfde000 r--p 00103000 00:12 7621                       /usr/lib/libX11.so.6.2.0
7f693bfde000-7f693bfe2000 rw-p 00104000 00:12 7621                       /usr/lib/libX11.so.6.2.0
7f693bfe2000-7f693c012000 r-xp 00000000 00:12 8479                       /usr/lib/libfontconfig.so.1.3.0
7f693c012000-7f693c212000 ---p 00030000 00:12 8479                       /usr/lib/libfontconfig.so.1.3.0
7f693c212000-7f693c213000 r--p 00030000 00:12 8479                       /usr/lib/libfontconfig.so.1.3.0
7f693c213000-7f693c214000 rw-p 00031000 00:12 8479                       /usr/lib/libfontconfig.so.1.3.0
7f693c214000-7f693c292000 r-xp 00000000 00:12 8477                       /usr/lib/libfreetype.so.6.3.18
7f693c292000-7f693c492000 ---p 0007e000 00:12 8477                       /usr/lib/libfreetype.so.6.3.18
7f693c492000-7f693c497000 r--p 0007e000 00:12 8477                       /usr/lib/libfreetype.so.6.3.18
7f693c497000-7f693c498000 rw-p 00083000 00:12 8477                       /usr/lib/libfreetype.so.6.3.18
7f693c498000-7f693c510000 r-xp 00000000 00:12 8473                       /usr/lib/libcairo.so.2.10800.0
7f693c510000-7f693c710000 ---p 00078000 00:12 8473                       /usr/lib/libcairo.so.2.10800.0
7f693c710000-7f693c712000 r--p 00078000 00:12 8473                       /usr/lib/libcairo.so.2.10800.0
7f693c712000-7f693c713000 rw-p 0007a000 00:12 8473                       /usr/lib/libcairo.so.2.10800.0
7f693c713000-7f693c787000 r-xp 00000000 00:12 8428                       /usr/lib/libgio-2.0.so.0.1800.2
7f693c787000-7f693c986000 ---p 00074000 00:12 8428                       /usr/lib/libgio-2.0.so.0.1800.2
7f693c986000-7f693c988000 r--p 00073000 00:12 8428                       /usr/lib/libgio-2.0.so.0.1800.2
7f693c988000-7f693c989000 rw-p 00075000 00:12 8428                       /usr/lib/libgio-2.0.so.0.1800.2
7f693c989000-7f693c98a000 rw-p 7f693c989000 00:00 0 
7f693c98a000-7f693c995000 r-xp 00000000 00:12 8469                       /usr/lib/libpangocairo-1.0.so.0.2201.0
7f693c995000-7f693cb94000 ---p 0000b000 00:12 8469                       /usr/lib/libpangocairo-1.0.so.0.2201.0
7f693cb94000-7f693cb95000 r--p 0000a000 00:12 8469                       /usr/lib/libpangocairo-1.0.so.0.2201.0
7f693cb95000-7f693cb96000 rw-p 0000b000 00:12 8469                       /usr/lib/libpangocairo-1.0.so.0.2201.0
7f693cb96000-7f693cbb0000 r-xp 00000000 00:12 8467                       /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
7f693cbb0000-7f693cdb0000 ---p 0001a000 00:12 8467                       /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
7f693cdb0000-7f693cdb1000 r--p 0001a000 00:12 8467                       /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
7f693cdb1000-7f693cdb2000 rw-p 0001b000 00:12 8467                       /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
7f693cdb2000-7f693cddd000 r-xp 00000000 00:12 8461                       /usr/lib/libpangoft2-1.0.so.0.2201.0
7f693cddd000-7f693cfdd000 ---p 0002b000 00:12 8461                       /usr/lib/libpangoft2-1.0.so.0.2201.0
7f693cfdd000-7f693cfde000 r--p 0002b000 00:12 8461                       /usr/lib/libpangoft2-1.0.so.0.2201.0
7f693cfde000-7f693cfdf000 rw-p 0002c000 00:12 8461                       /usr/lib/libpangoft2-1.0.so.0.2201.0
7f693cfdf000-7f693cffd000 r-xp 00000000 00:12 8459                       /usr/lib/libatk-1.0.so.0.2409.1
7f693cffd000-7f693d1fc000 ---p 0001e000 00:12 8459                       /usr/lib/libatk-1.0.so.0.2409.1
7f693d1fc000-7f693d1ff000 r--p 0001d000 00:12 8459                       /usr/lib/libatk-1.0.so.0.2409.1
7f693d1ff000-7f693d200000 rw-p 00020000 00:12 8459                       /usr/lib/libatk-1.0.so.0.2409.1
7f693d200000-7f693d29b000 r-xp 00000000 00:12 8465                       /usr/lib/libgdk-x11-2.0.so.0.1400.4
7f693d29b000-7f693d49b000 ---p 0009b000 00:12 8465                       /usr/lib/libgdk-x11-2.0.so.0.1400.4
7f693d49b000-7f693d49f000 r--p 0009b000 00:12 8465                       /usr/lib/libgdk-x11-2.0.so.0.1400.4
7f693d49f000-7f693d4a1000 rw-p 0009f000 00:12 8465                       /usr/lib/libgdk-x11-2.0.so.0.1400.4
7f693d4a1000-7f693d87b000 r-xp 00000000 00:12 8453                       /usr/lib/libgtk-x11-2.0.so.0.1400.4
7f693d87b000-7f693da7b000 ---p 003da000 00:12 8453                       /usr/lib/libgtk-x11-2.0.so.0.1400.4
7f693da7b000-7f693da82000 r--p 003da000 00:12 8453                       /usr/lib/libgtk-x11-2.0.so.0.1400.4
7f693da82000-7f693da86000 rw-p 003e1000 00:12 8453                       /usr/lib/libgtk-x11-2.0.so.0.1400.4
7f693da86000-7f693da88000 rw-p 7f693da86000 00:00 0 
7f693da88000-7f693dcb0000 r-xp 00000000 00:12 20914                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/gtk/_gtk.so
7f693dcb0000-7f693deaf000 ---p 00228000 00:12 20914                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/gtk/_gtk.so
7f693deaf000-7f693ded0000 r--p 00227000 00:12 20914                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/gtk/_gtk.so
7f693ded0000-7f693defd000 rw-p 00248000 00:12 20914                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/gtk/_gtk.so
7f693defd000-7f693defe000 rw-p 7f693defd000 00:00 0 
7f693defe000-7f693df1e000 r-xp 00000000 00:12 20870                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gobject/_gobject.so
7f693df1e000-7f693e11d000 ---p 00020000 00:12 20870                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gobject/_gobject.so
7f693e11d000-7f693e11e000 r--p 0001f000 00:12 20870                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gobject/_gobject.so
7f693e11e000-7f693e121000 rw-p 00020000 00:12 20870                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/gobject/_gobject.so
7f693e121000-7f693e122000 rw-p 7f693e121000 00:00 0 
7f693e122000-7f693e129000 r-xp 00000000 00:12 20859                      /usr/lib/libffi.so.5.0.6
7f693e129000-7f693e329000 ---p 00007000 00:12 20859                      /usr/lib/libffi.so.5.0.6
7f693e329000-7f693e32a000 rw-p 00007000 00:12 20859                      /usr/lib/libffi.so.5.0.6
7f693e32a000-7f693e332000 r-xp 00000000 00:12 275                        /lib/librt-2.8.90.so
7f693e332000-7f693e531000 ---p 00008000 00:12 275                        /lib/librt-2.8.90.so
7f693e531000-7f693e532000 r--p 00007000 00:12 275                        /lib/librt-2.8.90.so
7f693e532000-7f693e533000 rw-p 00008000 00:12 275                        /lib/librt-2.8.90.so
7f693e533000-7f693e537000 r-xp 00000000 00:12 518                        /usr/lib/libgthread-2.0.so.0.1800.2
7f693e537000-7f693e736000 ---p 00004000 00:12 518                        /usr/lib/libgthread-2.0.so.0.1800.2
7f693e736000-7f693e737000 r--p 00003000 00:12 518                        /usr/lib/libgthread-2.0.so.0.1800.2
7f693e737000-7f693e738000 rw-p 00004000 00:12 518                        /usr/lib/libgthread-2.0.so.0.1800.2
7f693e738000-7f693e73c000 r-xp 00000000 00:12 20857                      /usr/lib/pygobject/python2.5/libpyglib-2.0.so.0.0.0
7f693e73c000-7f693e93b000 ---p 00004000 00:12 20857                      /usr/lib/pygobject/python2.5/libpyglib-2.0.so.0.0.0
7f693e93b000-7f693e93c000 r--p 00003000 00:12 20857                      /usr/lib/pygobject/python2.5/libpyglib-2.0.so.0.0.0
7f693e93c000-7f693e93d000 rw-p 00004000 00:12 20857                      /usr/lib/pygobject/python2.5/libpyglib-2.0.so.0.0.0
7f693e93d000-7f693e94c000 r-xp 00000000 00:12 20850                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/glib/_glib.so
7f693e94c000-7f693eb4c000 ---p 0000f000 00:12 20850                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/glib/_glib.so
7f693eb4c000-7f693eb4d000 r--p 0000f000 00:12 20850                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/glib/_glib.so
7f693eb4d000-7f693eb50000 rw-p 00010000 00:12 20850                      /usr/lib/python-support/python-gobject/python2.5/gtk-2.0/glib/_glib.so
7f693eb50000-7f693eb78000 r-xp 00000000 00:12 243                        /lib/libpcre.so.3.12.1
7f693eb78000-7f693ed77000 ---p 00028000 00:12 243                        /lib/libpcre.so.3.12.1
7f693ed77000-7f693ed78000 r--p 00027000 00:12 243                        /lib/libpcre.so.3.12.1
7f693ed78000-7f693ed79000 rw-p 00028000 00:12 243                        /lib/libpcre.so.3.12.1
7f693ed79000-7f693ee3c000 r-xp 00000000 00:12 520                        /usr/lib/libglib-2.0.so.0.1800.2
7f693ee3c000-7f693f03b000 ---p 000c3000 00:12 520                        /usr/lib/libglib-2.0.so.0.1800.2
7f693f03b000-7f693f03c000 r--p 000c2000 00:12 520                        /usr/lib/libglib-2.0.so.0.1800.2
7f693f03c000-7f693f03d000 rw-p 000c3000 00:12 520                        /usr/lib/libglib-2.0.so.0.1800.2
7f693f03d000-7f693f03e000 rw-p 7f693f03d000 00:00 0 
7f693f03e000-7f693f041000 r-xp 00000000 00:12 524                        /usr/lib/libgmodule-2.0.so.0.1800.2
7f693f041000-7f693f240000 ---p 00003000 00:12 524                        /usr/lib/libgmodule-2.0.so.0.1800.2
7f693f240000-7f693f241000 r--p 00002000 00:12 524                        /usr/lib/libgmodule-2.0.so.0.1800.2
7f693f241000-7f693f242000 rw-p 00003000 00:12 524                        /usr/lib/libgmodule-2.0.so.0.1800.2
7f693f242000-7f693f286000 r-xp 00000000 00:12 530                        /usr/lib/libgobject-2.0.so.0.1800.2
7f693f286000-7f693f485000 ---p 00044000 00:12 530                        /usr/lib/libgobject-2.0.so.0.1800.2
7f693f485000-7f693f486000 r--p 00043000 00:12 530                        /usr/lib/libgobject-2.0.so.0.1800.2
7f693f486000-7f693f487000 rw-p 00044000 00:12 530                        /usr/lib/libgobject-2.0.so.0.1800.2
7f693f487000-7f693f488000 rw-p 7f693f487000 00:00 0 
7f693f488000-7f693f4ce000 r-xp 00000000 00:12 8471                       /usr/lib/libpango-1.0.so.0.2201.0
7f693f4ce000-7f693f6ce000 ---p 00046000 00:12 8471                       /usr/lib/libpango-1.0.so.0.2201.0
7f693f6ce000-7f693f6d0000 r--p 00046000 00:12 8471                       /usr/lib/libpango-1.0.so.0.2201.0
7f693f6d0000-7f693f6d1000 rw-p 00048000 00:12 8471                       /usr/lib/libpango-1.0.so.0.2201.0
7f693f6d1000-7f693f6f3000 r-xp 00000000 00:12 20966                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pango.so
7f693f6f3000-7f693f8f3000 ---p 00022000 00:12 20966                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pango.so
7f693f8f3000-7f693f8f6000 r--p 00022000 00:12 20966                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pango.so
7f693f8f6000-7f693f8fb000 rw-p 00025000 00:12 20966                      /usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pango.so
7f693f8fb000-7f693f912000 r-xp 00000000 00:12 522                        /usr/lib/libz.so.1.2.3.3
7f693f912000-7f693fb11000 ---p 00017000 00:12 522                        /usr/lib/libz.so.1.2.3.3
7f693fb11000-7f693fb13000 rw-p 00016000 00:12 522                        /usr/lib/libz.so.1.2.3.3
7f693fb13000-7f693fc76000 r-xp 00000000 00:12 8426                       /usr/lib/libcrypto.so.0.9.8
7f693fc76000-7f693fe75000 ---p 00163000 00:12 8426                       /usr/lib/libcrypto.so.0.9.8
7f693fe75000-7f693fe82000 r--p 00162000 00:12 8426                       /usr/lib/libcrypto.so.0.9.8
7f693fe82000-7f693fe98000 rw-p 0016f000 00:12 8426                       /usr/lib/libcrypto.so.0.9.8
7f693fe98000-7f693fe9c000 rw-p 7f693fe98000 00:00 0 
7f693fe9c000-7f693fee5000 r-xp 00000000 00:12 8421                       /usr/lib/libssl.so.0.9.8
7f693fee5000-7f69400e5000 ---p 00049000 00:12 8421                       /usr/lib/libssl.so.0.9.8
7f69400e5000-7f69400e6000 r--p 00049000 00:12 8421                       /usr/lib/libssl.so.0.9.8
7f69400e6000-7f69400eb000 rw-p 0004a000 00:12 8421                       /usr/lib/libssl.so.0.9.8
7f69400eb000-7f69400ef000 r-xp 00000000 00:12 21922                      /usr/lib/python2.5/lib-dynload/_ssl.so
7f69400ef000-7f69402ee000 ---p 00004000 00:12 21922                      /usr/lib/python2.5/lib-dynload/_ssl.so
7f69402ee000-7f69402ef000 r--p 00003000 00:12 21922                      /usr/lib/python2.5/lib-dynload/_ssl.so
7f69402ef000-7f69402f0000 rw-p 00004000 00:12 21922                      /usr/lib/python2.5/lib-dynload/_ssl.so
7f69402f0000-7f69402fc000 r-xp 00000000 00:12 21921                      /usr/lib/python2.5/lib-dynload/_socket.so
7f69402fc000-7f69404fb000 ---p 0000c000 00:12 21921                      /usr/lib/python2.5/lib-dynload/_socket.so
7f69404fb000-7f69404fc000 r--p 0000b000 00:12 21921                      /usr/lib/python2.5/lib-dynload/_socket.so
7f69404fc000-7f6940500000 rw-p 0000c000 00:12 21921                      /usr/lib/python2.5/lib-dynload/_socket.so
7f6940500000-7f69405c1000 rw-p 7f6940500000 00:00 0 
7f69405c1000-7f69405c4000 r-xp 00000000 00:12 484                        /usr/lib/python2.5/lib-dynload/math.so
7f69405c4000-7f69407c3000 ---p 00003000 00:12 484                        /usr/lib/python2.5/lib-dynload/math.so
7f69407c3000-7f69407c4000 r--p 00002000 00:12 484                        /usr/lib/python2.5/lib-dynload/math.so
7f69407c4000-7f69407c5000 rw-p 00003000 00:12 484                        /usr/lib/python2.5/lib-dynload/math.so
7f69407c5000-7f69407d7000 r-xp 00000000 00:12 22387                      /usr/lib/python2.5/lib-dynload/datetime.so
7f69407d7000-7f69409d6000 ---p 00012000 00:12 22387                      /usr/lib/python2.5/lib-dynload/datetime.so
7f69409d6000-7f69409d7000 r--p 00011000 00:12 22387                      /usr/lib/python2.5/lib-dynload/datetime.so
7f69409d7000-7f69409db000 rw-p 00012000 00:12 22387                      /usr/lib/python2.5/lib-dynload/datetime.so
7f69409db000-7f69409df000 r-xp 00000000 00:12 1913                       /usr/lib/python2.5/lib-dynload/cStringIO.so
7f69409df000-7f6940bde000 ---p 00004000 00:12 1913                       /usr/lib/python2.5/lib-dynload/cStringIO.so
7f6940bde000-7f6940bdf000 r--p 00003000 00:12 1913                       /usr/lib/python2.5/lib-dynload/cStringIO.so
7f6940bdf000-7f6940be1000 rw-p 00004000 00:12 1913                       /usr/lib/python2.5/lib-dynload/cStringIO.so
7f6940be1000-7f6940be6000 r-xp 00000000 00:12 485                        /usr/lib/python2.5/lib-dynload/binascii.so
7f6940be6000-7f6940de5000 ---p 00005000 00:12 485                        /usr/lib/python2.5/lib-dynload/binascii.so
7f6940de5000-7f6940de6000 r--p 00004000 00:12 485                        /usr/lib/python2.5/lib-dynload/binascii.so
7f6940de6000-7f6940de7000 rw-p 00005000 00:12 485                        /usr/lib/python2.5/lib-dynload/binascii.so
7f6940de7000-7f6940dea000 r-xp 00000000 00:12 1910                       /usr/lib/python2.5/lib-dynload/select.so
7f6940dea000-7f6940fe9000 ---p 00003000 00:12 1910                       /usr/lib/python2.5/lib-dynload/select.so
7f6940fe9000-7f6940fea000 r--p 00002000 00:12 1910                       /usr/lib/python2.5/lib-dynload/select.so
7f6940fea000-7f6940feb000 rw-p 00003000 00:12 1910                       /usr/lib/python2.5/lib-dynload/select.so
7f6940feb000-7f6940fef000 r-xp 00000000 00:12 1909                       /usr/lib/python2.5/lib-dynload/time.so
7f6940fef000-7f69411ee000 ---p 00004000 00:12 1909                       /usr/lib/python2.5/lib-dynload/time.so
7f69411ee000-7f69411ef000 r--p 00003000 00:12 1909                       /usr/lib/python2.5/lib-dynload/time.so
7f69411ef000-7f69411f1000 rw-p 00004000 00:12 1909                       /usr/lib/python2.5/lib-dynload/time.so
7f69411f1000-7f69411f8000 r-xp 00000000 00:12 1081                       /usr/lib/python2.5/lib-dynload/_struct.so
7f69411f8000-7f69413f7000 ---p 00007000 00:12 1081                       /usr/lib/python2.5/lib-dynload/_struct.so
7f69413f7000-7f69413f8000 r--p 00006000 00:12 1081                       /usr/lib/python2.5/lib-dynload/_struct.so
7f69413f8000-7f69413fa000 rw-p 00007000 00:12 1081                       /usr/lib/python2.5/lib-dynload/_struct.so
7f69413fa000-7f6941401000 r-xp 00000000 00:12 1076                       /usr/lib/python2.5/lib-dynload/operator.so
7f6941401000-7f6941600000 ---p 00007000 00:12 1076                       /usr/lib/python2.5/lib-dynload/operator.so
7f6941600000-7f6941601000 r--p 00006000 00:12 1076                       /usr/lib/python2.5/lib-dynload/operator.so
7f6941601000-7f6941603000 rw-p 00007000 00:12 1076                       /usr/lib/python2.5/lib-dynload/operator.so
7f6941603000-7f6941607000 r-xp 00000000 00:12 1075                       /usr/lib/python2.5/lib-dynload/_locale.so
7f6941607000-7f6941806000 ---p 00004000 00:12 1075                       /usr/lib/python2.5/lib-dynload/_locale.so
7f6941806000-7f6941807000 r--p 00003000 00:12 1075                       /usr/lib/python2.5/lib-dynload/_locale.so
7f6941807000-7f6941808000 rw-p 00004000 00:12 1075                       /usr/lib/python2.5/lib-dynload/_locale.so
7f6941808000-7f694180d000 r-xp 00000000 00:12 1070                       /usr/lib/python2.5/lib-dynload/strop.so
7f694180d000-7f6941a0c000 ---p 00005000 00:12 1070                       /usr/lib/python2.5/lib-dynload/strop.so
7f6941a0c000-7f6941a0d000 r--p 00004000 00:12 1070                       /usr/lib/python2.5/lib-dynload/strop.so
7f6941a0d000-7f6941a0f000 rw-p 00005000 00:12 1070                       /usr/lib/python2.5/lib-dynload/strop.so
7f6941a0f000-7f6941a11000 r-xp 00000000 00:12 22361                      /usr/lib/python2.5/lib-dynload/syslog.so
7f6941a11000-7f6941c10000 ---p 00002000 00:12 22361                      /usr/lib/python2.5/lib-dynload/syslog.so
7f6941c10000-7f6941c11000 r--p 00001000 00:12 22361                      /usr/lib/python2.5/lib-dynload/syslog.so
7f6941c11000-7f6941c12000 rw-p 00002000 00:12 22361                      /usr/lib/python2.5/lib-dynload/syslog.so
7f6941c12000-7f6941c15000 r-xp 00000000 00:12 487                        /usr/lib/python2.5/lib-dynload/fcntl.so
7f6941c15000-7f6941e14000 ---p 00003000 00:12 487                        /usr/lib/python2.5/lib-dynload/fcntl.so
7f6941e14000-7f6941e15000 r--p 00002000 00:12 487                        /usr/lib/python2.5/lib-dynload/fcntl.so
7f6941e15000-7f6941e16000 rw-p 00003000 00:12 487                        /usr/lib/python2.5/lib-dynload/fcntl.so
7f6941e16000-7f6941f7f000 r-xp 00000000 00:12 37                         /lib/libc-2.8.90.so
7f6941f7f000-7f694217e000 ---p 00169000 00:12 37                         /lib/libc-2.8.90.so
7f694217e000-7f6942182000 r--p 00168000 00:12 37                         /lib/libc-2.8.90.so
7f6942182000-7f6942183000 rw-p 0016c000 00:12 37                         /lib/libc-2.8.90.so
7f6942183000-7f6942188000 rw-p 7f6942183000 00:00 0 
7f6942188000-7f694220c000 r-xp 00000000 00:12 33                         /lib/libm-2.8.90.so
7f694220c000-7f694240b000 ---p 00084000 00:12 33                         /lib/libm-2.8.90.so
7f694240b000-7f694240c000 r--p 00083000 00:12 33                         /lib/libm-2.8.90.so
7f694240c000-7f694240d000 rw-p 00084000 00:12 33                         /lib/libm-2.8.90.so
7f694240d000-7f694240f000 r-xp 00000000 00:12 354                        /lib/libutil-2.8.90.so
7f694240f000-7f694260e000 ---p 00002000 00:12 354                        /lib/libutil-2.8.90.so
7f694260e000-7f694260f000 r--p 00001000 00:12 354                        /lib/libutil-2.8.90.so
7f694260f000-7f6942610000 rw-p 00002000 00:12 354                        /lib/libutil-2.8.90.so
7f6942610000-7f6942612000 r-xp 00000000 00:12 31                         /lib/libdl-2.8.90.so
7f6942612000-7f6942812000 ---p 00002000 00:12 31                         /lib/libdl-2.8.90.so
7f6942812000-7f6942813000 r--p 00002000 00:12 31                         /lib/libdl-2.8.90.so
7f6942813000-7f6942814000 rw-p 00003000 00:12 31                         /lib/libdl-2.8.90.so
7f6942814000-7f694282b000 r-xp 00000000 00:12 35                         /lib/libpthread-2.8.90.so
7f694282b000-7f6942a2a000 ---p 00017000 00:12 35                         /lib/libpthread-2.8.90.so
7f6942a2a000-7f6942a2b000 r--p 00016000 00:12 35                         /lib/libpthread-2.8.90.so
7f6942a2b000-7f6942a2c000 rw-p 00017000 00:12 35                         /lib/libpthread-2.8.90.so
7f6942a2c000-7f6942a30000 rw-p 7f6942a2c000 00:00 0 
7f6942a30000-7f6942a4f000 r-xp 00000000 00:12 25                         /lib/ld-2.8.90.so
7f6942a58000-7f6942a59000 rw-p 7f6942a58000 00:00 0 
7f6942a59000-7f6942a5a000 r--p 00000000 00:12 999                        /usr/lib/locale/en_CA.utf8/LC_NUMERIC
7f6942a5a000-7f6942a5b000 r--p 00000000 00:12 22940                      /usr/lib/locale/en_CA.utf8/LC_TIME
7f6942a5b000-7f6942a5c000 r--p 00000000 00:12 22938                      /usr/lib/locale/en_CA.utf8/LC_MONETARY
7f6942a5c000-7f6942a5d000 r--p 00000000 00:12 22937                      /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7f6942a5d000-7f6942a5e000 r--p 00000000 00:12 993                        /usr/lib/locale/en_CA.utf8/LC_PAPER
7f6942a5e000-7f6942a5f000 r--p 00000000 00:12 22935                      /usr/lib/locale/en_CA.utf8/LC_NAME
7f6942a5f000-7f6942a60000 r--p 00000000 00:12 22934                      /usr/lib/locale/en_CA.utf8/LC_ADDRESS
7f6942a60000-7f6942ac0000 rw-s 00000000 00:09 491534                     /SYSV00000000 (deleted)
7f6942ac0000-7f6942b01000 rw-p 7f6942ac0000 00:00 0 
7f6942b01000-7f6942b02000 r--p 00000000 00:12 22933                      /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
7f6942b02000-7f6942b03000 r--p 00000000 00:12 22932                      /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
7f6942b03000-7f6942b17000 r--p 00000000 00:12 22920                      /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_gu.ttf
7f6942b17000-7f6942b2e000 r--s 00000000 00:12 17089                      /usr/share/mime/mime.cache
7f6942b2e000-7f6942b37000 r--s 00000000 00:12 17064                      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
7f6942b37000-7f6942b3a000 r--s 00000000 00:12 17062                      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
7f6942b3a000-7f6942b3b000 r--s 00000000 00:12 17060                      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
7f6942b3b000-7f6942b3f000 r--s 00000000 00:12 17058                      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
7f6942b3f000-7f6942b43000 r--s 00000000 00:12 17056                      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
7f6942b43000-7f6942b46000 r--s 00000000 00:12 17053                      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
7f6942b46000-7f6942b51000 r--s 00000000 00:12 17051                      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
7f6942b51000-7f6942b60000 r--s 00000000 00:12 17047                      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
7f6942b60000-7f6942b61000 r--s 00000000 00:12 17045                      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
7f6942b61000-7f6942b64000 r--s 00000000 00:12 17043                      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
7f6942b64000-7f6942b6d000 r--s 00000000 00:12 17041                      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
7f6942b6d000-7f6942b74000 r--s 00000000 00:12 17039                      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
7f6942b74000-7f6942b7b000 r--s 00000000 00:12 535                        /usr/lib/gconv/gconv-modules.cache
7f6942b7b000-7f6942bba000 r--p 00000000 00:12 1000                       /usr/lib/locale/en_US.utf8/LC_CTYPE
7f6942bba000-7f6942c3f000 rw-p 7f6942bba000 00:00 0 
7f6942c3f000-7f6942c40000 r--p 00000000 00:12 934                        /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
7f6942c40000-7f6942c41000 r--p 00000000 00:12 999                        /usr/lib/locale/en_US.utf8/LC_NUMERIC
7f6942c41000-7f6942c42000 r--p 00000000 00:12 998                        /usr/lib/locale/en_US.utf8/LC_TIME
7f6942c42000-7f6942c43000 r--p 00000000 00:12 996                        /usr/lib/locale/en_US.utf8/LC_MONETARY
7f6942c43000-7f6942c44000 r--p 00000000 00:12 995                        /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7f6942c44000-7f6942c45000 r--p 00000000 00:12 993                        /usr/lib/locale/en_US.utf8/LC_PAPER
7f6942c45000-7f6942c46000 r--p 00000000 00:12 992                        /usr/lib/locale/en_US.utf8/LC_NAME
7f6942c46000-7f6942c47000 r--p 00000000 00:12 991                        /usr/lib/locale/en_US.utf8/LC_ADDRESS
7f6942c47000-7f6942c48000 r--p 00000000 00:12 990                        /usr/lib/locale/en_US.utf8/LC_TELEPHONE
7f6942c48000-7f6942c49000 r--p 00000000 00:12 989                        /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
7f6942c49000-7f6942c4a000 r--p 00000000 00:12 943                        /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
7f6942c4a000-7f6942c4e000 rw-p 7f6942c4a000 00:00 0 
7f6942c4e000-7f6942c4f000 r--p 0001e000 00:12 25                         /lib/ld-2.8.90.so
7f6942c4f000-7f6942c50000 rw-p 0001f000 00:12 25                         /lib/ld-2.8.90.so
7fff4ac24000-7fff4ac4f000 rw-p 7ffffffd4000 00:00 0                      [stack]
7fff4adfe000-7fff4adff000 r-xp 7fff4adfe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
```

Using synaptic it seems I have no broken packages and noting is marked for upgrades. 

Thanks

David

---

