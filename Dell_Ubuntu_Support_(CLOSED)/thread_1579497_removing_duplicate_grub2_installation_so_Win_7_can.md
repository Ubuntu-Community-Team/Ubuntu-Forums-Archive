---
title: "removing duplicate grub2 installation so Win 7 can boot"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spc456 on 2010-09-21
Hello,

I have a Dell Inspiron 1545 with Windows 7.

I installed Ubuntu 10.07, rebooted few times and all went well. Got connected to wireless internet and all.

Eventually, I turned off the computer and the next day I booted to Windows 7 all went well, however, I wanted to go back to Ubuntu and I could no longer boot on anything. 

There are other posts here in this Forum  mentioning that Dell DataSafe software maybe messing up grub’s boot loader.

But in the attempt of recovering grub I mistakenly installed grub on sda2 partition where Win 7 /Boot/BCD is located, please see the listing of RESULTS.txt below.
RESULTS.txt is the output of boot_info_script055.sh [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Now I have two grub2 bootloader: one at sda2 and one at sda6
The correct one is sda6.

I have fixed so I can boot Ubuntu 10.04.

However, with grub2 on sda2 I cannot boot Win 7; so is there a way to remove /boot/grub/grub.cfg and /boot/grub/core.img ?

I wonder if I can do this on the Ubuntu side:

```
sudo mkdir /media/gfb
```  

(gfb or any name)

```
sudo mount /dev/sda2 /media/gfb
```  

Then 

```
cd /media/gfb
```

Then 

```
mv /boot  /broken
``` 

or just 

```
rm –rf /boot
```

Would that work? :confused:

Thank you,

Mark

```

RESULTS.txt:
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 278432416 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /bootmgr /Boot/BCD 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   211,029,839   180,227,920   7 HPFS/NTFS
/dev/sda4         211,045,966   625,141,759   414,095,794   5 Extended
/dev/sda5         211,045,968   416,112,979   205,067,012   7 HPFS/NTFS
/dev/sda6         416,114,688   616,554,495   200,439,808  83 Linux
/dev/sda7         616,556,544   625,141,759     8,585,216  82 Linux swap / Solaris

```

---

### Post by drs305 on 2010-09-21
It looks like you are missing some of the W7 boot files. You will need to fix this with the W7 CD. I'll have to leave it to a W7 user to provide the details, or take a look around the forums.

This link may be enough, but I'm not sure how much you are missing:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by spc456 on 2010-09-22
Well, no takers so far but I have something to share:

Moving /boot to /broken in sda2 partition worked

```
  
sudo mkdir /media/gfb
sudo mount /dev/sda2 /media/gfb
cd /media/gfb
mv /boot  /broken

```

I decided to rename /boot for now.
Then I reinstalled grub2

```


mark@hws01:~$ sudo update-grub2
[sudo] password for mark: 
Generating grub.cfg ...
Found background image: Apollo_17_The_Last_Moon_Shot_Edit1.tga
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
mark@hws01:~$

```

Note that now Win 7 was picked up by grub2’s 30_os-prober (see boot_info_script055.sh listing).

Then I rebooted and grub2 came up for the first time with the my splash screen (Apollo_17_The_Last_Moon_Shot_Edit1.tga) and the OS menu options including Windows 7 loader.

I then rebooted to Ubuntu and all went well.
I have not booted to Windows 7 because I am still not sure why Win 7 corrupted grub2’s boot routine.

I will see if I can rename Dell’s DataSafe; the files that some people are saying is the cause of this problem, from Ubuntu side?

Here is the total listing of boot_info_script055.sh from the good folks of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please note that sda2 still lists grub2 installed in it. 

I wonder if /bootmgr belongs to grub2?

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 278432416 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   211,029,839   180,227,920   7 HPFS/NTFS
/dev/sda4         211,045,966   625,141,759   414,095,794   5 Extended
/dev/sda5         211,045,968   416,112,979   205,067,012   7 HPFS/NTFS
/dev/sda6         416,114,688   616,554,495   200,439,808  83 Linux
/dev/sda7         616,556,544   625,141,759     8,585,216  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders, total 494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  37       494,079       494,043   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        1AFA0F55FA0F2D17                       ntfs       RECOVERY                      
/dev/sda3        981E11881E116114                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        36668F7127125666                       ntfs       storage                       
/dev/sda6        84927fb4-fc19-4fee-bf99-ac630e201d41   ext4                                     
/dev/sda7        af1520f3-b6bd-4d88-9477-7c207f3bb472   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        FFFF-FFFF                              vfat       BLACKBERRY                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/BLACKBERRY        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
insmod play
play 580 480 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
insmod tga
if background_image /usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=84927fb4-fc19-4fee-bf99-ac630e201d41 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=84927fb4-fc19-4fee-bf99-ac630e201d41 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 84927fb4-fc19-4fee-bf99-ac630e201d41
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1afa0f55fa0f2d17
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=84927fb4-fc19-4fee-bf99-ac630e201d41 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=af1520f3-b6bd-4d88-9477-7c207f3bb472 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 264.7GB: boot/grub/core.img
 215.6GB: boot/grub/grub.cfg
 264.8GB: boot/initrd.img-2.6.32-24-generic-pae
 264.7GB: boot/vmlinuz-2.6.32-24-generic-pae
 264.8GB: initrd.img
 264.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

```

Thank you,:)

Mark

---

### Post by wilee-nilee on 2010-09-22
drs305 is correct your missing in sda3 this
/Windows/System32/winload.exe

In mine with the OS in one partition the line is this.
Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

This I believe can be dealt with, but by somebody who knows this stuff. Looks like you got the grub out of the ntfs though.

Also if you get W7 up and running remove the Dell Data Safe, you don't rename it. I think this was just a consideration from access at this point, I think you recognize that it will have to be removed.

I would try a thread at the 7 forums as well, it might get you in quicker.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

There are people over there dual booting as well. I think that this is a fairly easy fix if you have a install dvd, maybe even a recovery, it is just knowing how to do it.;)

The os-prober is seeing this, maybe more I don't know how that program actually works.
sda2  */bootmgr /Boot/BCD*
In the W7 booting partition, but the whole set is not there in the partition of W7s' OS.

---

### Post by topet2k12001 on 2010-11-01
> **spc456 said:**
> ...in the attempt of recovering grub I mistakenly installed grub on sda2 partition where Win 7 /Boot/BCD is located, please see the listing of 
 
Now I have two grub2 bootloader: one at sda2 and one at sda6
The correct one is sda6.
 
I have fixed so I can boot Ubuntu 10.04.
 
However, with grub2 on sda2 I cannot boot Win 7; so is there a way to remove /boot/grub/grub.cfg and /boot/grub/core.img ?

 
Hi Friend,
 
As far as the only quoted part of your message goes...I've had the same problem today...but it took me a long time to realize that I ended up installing two sets of GRUB2, lol... :D What happened was it prevented me from seeing the GRUB2 Boot Screen and my computer goes straight to booting into Ubuntu. Perhaps it was because GRUB2 was not able to find "any other OS" via the os-probe.
 
So I've searched around and found an answer that I didn't realize was the answer to my problem until it hit me. It was also here in the Ubuntu Forums (whoever that was I would like to thank him unfortunately I forgot the thread title). The answer to the problem was because a folder named "boot" (one created when GRUB2 was installed twice) and "Boot" (the Boot folder in Windows 7) exists in the same partition (in your case it could be sda2). Based on the post of the person I was reading off from, NTFS file systems are not case-sensitive so it couldn't distinguish between "boot" with a small "b" or capital "B".
 
What I did is:
 
1. Boot from a Live USB or CD (mine was USB)
2. Opened File Manager
3. Deleted the "boot" folder (the one with a small "b" which was created by GRUB 2)
4. Enter the command ```
sudo update-grub
``` from the Terminal
5. Reboot the computer
 
I've read through this thread and you may have some other problems relating to missing files, but I just wanted to share this because a specific part of your posts was my exact problem earlier; I hope this may have helped you in any way. :)

EDIT: I found the thread I was reading the solution from: [http://ubuntuforums.org/showthread.php?p=10057577#post10057577](http://ubuntuforums.org/showthread.php?p=10057577#post10057577). It's on the 5th post. Hope this helps. :)

---

