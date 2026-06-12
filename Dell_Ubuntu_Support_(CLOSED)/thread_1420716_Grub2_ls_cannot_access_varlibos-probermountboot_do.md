---
title: "Grub2 ls: cannot access /var/lib/os-prober/mount/boot doesn't see Win7"
date: 2010-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eliemicb on 2010-03-03
Hello there, 

Laptop Dell Studio 1555.
The cause: I started an app called Dell DataSafe Local Backup. 
The result: Grub2 couldn't find a symbol. 
The solution: Reinstalling Grub2. 

After I figured out getting my Grub2 to run again, I could boot Ubuntu, but not Win7. 
So I inserted the Win7 recovery DVD and used fixmbr and FixBoot in the commandline, and there Win7 was bootable again, but without Grub2 and Ubuntu. 

I am able to start both OS's, but with a LOT of effort. 
Thinking that it has to be able getting work again, I reinstalled Grub2 once more. 
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
```I already found a thread with the same error message: 
[http://ubuntuforums.org/showthread.php?t=1374445]("http://http://ubuntuforums.org/showthread.php?t=1374445")
but I don't see the solution, because I didn't find a low case /boot folder on my Win7 partition. 

Here is what I get using the BootInfoScript([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/))
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grub/core.img /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10264032

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   174,160,664   143,360,340   7 HPFS/NTFS
/dev/sda4         174,160,665   976,768,064   802,607,400   f W95 Ext d (LBA)
/dev/sda5         174,163,968   522,323,967   348,160,000   7 HPFS/NTFS
/dev/sda6         522,326,016   870,486,015   348,160,000   7 HPFS/NTFS
/dev/sda7         870,498,153   972,334,124   101,835,972  83 Linux
/dev/sda8         972,334,188   976,768,064     4,433,877  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        2A2AA7362AA6FE47                       ntfs       RECOVERY                      
/dev/sda3        36A2AA85A2AA48E7                       ntfs       OS                            
/dev/sda5        3868A3E668A3A0DC                       ntfs       Games                         
/dev/sda6        320CB7450CB70341                       ntfs       Data                          
/dev/sda7        3d0b9ff8-34cc-4630-bf3e-42ea7745102c   ext4                                     
/dev/sda8        9e9f3c8d-525d-43d7-b3fa-0357bfd504c8   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 3d0b9ff8-34cc-4630-bf3e-42ea7745102c
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3d0b9ff8-34cc-4630-bf3e-42ea7745102c
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=3d0b9ff8-34cc-4630-bf3e-42ea7745102c ro   quiet splash nolapic
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3d0b9ff8-34cc-4630-bf3e-42ea7745102c
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=3d0b9ff8-34cc-4630-bf3e-42ea7745102c ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3d0b9ff8-34cc-4630-bf3e-42ea7745102c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=3d0b9ff8-34cc-4630-bf3e-42ea7745102c ro   quiet splash nolapic
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3d0b9ff8-34cc-4630-bf3e-42ea7745102c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=3d0b9ff8-34cc-4630-bf3e-42ea7745102c ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#!/bin/sh exec tail -n +3 $0 (-)
# This file is an example on how to add custom entries
menuentry "Windows 7" {
insmod chain
insmod ntfs
search --fs-uuid --set 36a2aa85a2aa48e7
drivemap -s hd0 hd1
chainloader +1
}
  
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=3d0b9ff8-34cc-4630-bf3e-42ea7745102c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9e9f3c8d-525d-43d7-b3fa-0357bfd504c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 446.6GB: boot/grub/core.img
 446.7GB: boot/grub/grub.cfg
 447.6GB: boot/initrd.img-2.6.31-17-generic
 446.7GB: boot/initrd.img-2.6.31-19-generic
 445.9GB: boot/vmlinuz-2.6.31-17-generic
 447.3GB: boot/vmlinuz-2.6.31-19-generic
 446.7GB: initrd.img
 447.6GB: initrd.img.old
 447.3GB: vmlinuz
 445.9GB: vmlinuz.old
```Because I am now at one's wits' end, I am consulting you, folks.

---

### Post by josealfredo1515 on 2010-05-02
Hi, I had the same problem but I found a solution here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows), the only thing you have to do is to rename a folder named "boot" on the System Reserved patition

---

### Post by oldfred on 2010-05-02
You somehow got grub files in your windows boot.

sda2
Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/grub/core.img /boot/grub/core.img[/COLOR]

If sda2 is not the boot partition but recovery as the label says then you are missing these from sda3.
/bootmgr /Boot/BCD

sda2 also has the boot flag which would indicate it is a boot directory, but boot directories for windows are only 100k. 

You have a 40_custom pointing the second drive, but did not have it plugged in when you ran the script.

I am not sure if you boot thru sda2 or need to move the boot flag to sda3 and run repairs on sda3. Either way remove the files in sda2 that are from grub.

Sees this if running Dell:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)

---

### Post by eli.bad on 2010-11-05
> **josealfredo1515 said:**
> Hi, I had the same problem but I found a solution here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows), the only thing you have to do is to rename a folder named "boot" on the System Reserved patition


Man ! I had to reinstall grub- then reinstall windows and had a whole mess before I found such an easy and effective solution!!!

Grub2 is a mess!

---

### Post by JPWhite on 2010-11-13
> **josealfredo1515 said:**
> Hi, I had the same problem but I found a solution here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows), the only thing you have to do is to rename a folder named "boot" on the System Reserved patition

Brilliant!! Thanks so much, this simple fix allowed me to get my dual boot system back to normal, my update-grub was also not working due to my repeated and eventually successful attempts to rebuild Grub2 after cloning to a new hard drive.

---

### Post by H2G on 2010-11-17
> **jpwhite said:**
> brilliant!! Thanks so much, this simple fix allowed me to get my dual boot system back to normal (...)
+1

---

### Post by tophousetim on 2011-03-02
Thanks josealfredo1515.......fixed my problem easily and without too much stress.
I'm [Solved]:popcorn:

---

### Post by ds_mart on 2011-06-04
Thank you for the advice, this worked for me as well.  MS has changed the boot process in Windows 7, using a separate boot partition.  It appears that GRUB2/os-prober cannot properly identify this new design.  Consequently, Windows fails to appear on the Grub2 boot menu.

---

