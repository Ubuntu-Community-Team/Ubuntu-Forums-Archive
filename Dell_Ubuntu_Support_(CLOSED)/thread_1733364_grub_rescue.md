---
title: "grub rescue"
date: 2011-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ishuA on 2011-04-19
i have a dell inspiron n5010 laptop having dual boot(windows 7 and ubuntu 10.10).Recently i deleted a ntfs partition in windows which had nothing to do with boot process .After reboot i came across a grub rescue prompt saying no such partition found....i could not boot into either of the two OS.I rescued into windows by fixing the MBR,but now i cannot boot into ubuntu (i was knowing dat i wont b able to after i do this)..i have data stored in home folder in ubuntu and i cant afford to loose them....plzzz help...

---

### Post by Rubi1200 on 2011-04-19
Hi and welcome to the forums :-)

Please do the following so we can get a better view of the current state of the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ishuA on 2011-04-19
sir,
   i tried to boot using live cd...but got following error message...

busy box v1.15.3 (Ubuntu 1:1.15.3 - 1ubuntu5 ) built in shell (ash)
Enter 'help' for a list of commands

(initramfs) mount:mounting /dev/loop0 on //filesystem.squashfs failed : Input/Output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on // filesystem.squashfs

---

### Post by Rubi1200 on 2011-04-19
Okay, there could be few possible reasons for this.

Is BIOS set to boot from the CD drive?

You should check the integrity of the CD:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you burn at the lowest possible speed?

---

### Post by ishuA on 2011-04-19
my bios is set to boot from the cd drive....and i have already used the cd several times for installation as well as live cd....

---

### Post by Rubi1200 on 2011-04-19
Okay, next suggestion.

Download and burn to CD another Linux distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

You can then try and use this as a LiveCD to boot the computer.

If it works, run the script I posted about before, but you do not need to use sudo in the command because the terminal on Slax has root permissions by default.

---

### Post by ishuA on 2011-04-20
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x504ae195

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    64,514,047    64,307,200   7 HPFS/NTFS
/dev/sda3          64,514,048   310,274,047   245,760,000   7 HPFS/NTFS
/dev/sda4         310,276,094   494,069,759   183,793,666   f W95 Ext d (LBA)
/dev/sda5         397,389,824   413,990,911    16,601,088  82 Linux swap / Solaris
/dev/sda6         413,992,960   494,069,759    80,076,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2461793461786F7                       ntfs       System Reserved               
/dev/sda2        46B61DC7B61DB87F                       ntfs       Windows7                      
/dev/sda3        CE96ECE496ECCDD1                       ntfs       Entertainment                 
/dev/sda5        9d114869-bed7-462e-ae89-3a2a6f8e246c   swap                                     
/dev/sda6        4c1183e7-1f26-46b5-9f67-82b256fc96ed   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=5a10810a,xino=/mnt/live/memory/.aufs.xino,nowarn_perm)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)
/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda3        /mnt/sda3                fuseblk    (rw,noatime,allow_other,blksize=4096)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 40  31 05 00 50 fd 00 00 fe  |.......@1..P....|
000001d0  ff ff 05 fe ff ff 02 90  2e 06 00 e8 c5 04 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file

---

### Post by ishuA on 2011-04-20
i would be highly greatful if u provide me a solution which helps me to dual boot my system

---

### Post by Rubi1200 on 2011-04-20
Thanks for the results. I assume Windows is boot normally right?

The problem appears to be with what I assume is the Ubuntu install on sda6:
> mount: unknown filesystem type 'ext4'

Do you have backups of your data from Ubuntu?

You can use the Slax LiveCD to run the following command to try and fix the file-system:
```
e2fsck -f -y -v /dev/sda6
```
Let the command run until it is done and then while still on the CD run the results of the script as you did before and post it here again.

If the command has fixed the file-system, then we should be able to reinstall GRUB and get you going again.

But, as with anything else like this, there is a chance it won't work and you may have to do a clean install of Ubuntu again.

---

### Post by ishuA on 2011-04-20
i dont have a back up of data in home folder of ubuntu,.....i cant afford to loose dem...
if u can help me access those data thru window it can be of great help....by that time let me try the task you want me to

---

### Post by ishuA on 2011-04-20
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x504ae195

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    64,514,047    64,307,200   7 HPFS/NTFS
/dev/sda3          64,514,048   310,274,047   245,760,000   7 HPFS/NTFS
/dev/sda4         310,276,094   494,069,759   183,793,666   f W95 Ext d (LBA)
/dev/sda5         397,389,824   413,990,911    16,601,088  82 Linux swap / Solaris
/dev/sda6         413,992,960   494,069,759    80,076,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2461793461786F7                       ntfs       System Reserved               
/dev/sda2        46B61DC7B61DB87F                       ntfs       Windows7                      
/dev/sda3        CE96ECE496ECCDD1                       ntfs       Entertainment                 
/dev/sda5        9d114869-bed7-462e-ae89-3a2a6f8e246c   swap                                     
/dev/sda6        4c1183e7-1f26-46b5-9f67-82b256fc96ed   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=5b8ce8b5,xino=/mnt/live/memory/.aufs.xino,nowarn_perm)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)
/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda3        /mnt/sda3                fuseblk    (rw,noatime,allow_other,blksize=4096)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 40  31 05 00 50 fd 00 00 fe  |.......@1..P....|
000001d0  ff ff 05 fe ff ff 02 90  2e 06 00 e8 c5 04 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file

---

### Post by ishuA on 2011-04-20
both reports seem same to me ...plzz provide me a process in which i can atleast retrieve my data from the home folder

---

### Post by ishuA on 2011-04-20
[I]when i try to access the home folder partition thru slax i get the following error

[/I]> 
mount : wrong fs type ,bad option,bad superblock in /dev/sda6,
missing code page or helper program,or other error
In some cases useful info is found in syslog-trydmesg I tail or so




---

### Post by oldfred on 2011-04-20
There is no way from windows to get data from an ext4 partition. 

Did you run the e2fsck commands Rubi1200 gave you. That has the best chance of getting your data back.

---

### Post by ishuA on 2011-04-21
I have already tried repairing the filesystem as said by rubi1200 and i have also pasted the result .......

---

### Post by ishuA on 2011-04-21
we can actually access the ubuntu partition from windows as well as slax...
for slax....heres the link

[http://www.slax.org/forum.php?action=view&parentID=40460&highlight=ext4http://www.slax.org/forum.php?action=view&parentID=40460&highlight=ext4](http://www.slax.org/forum.php?action=view&parentID=40460&highlight=ext4http://www.slax.org/forum.php?action=view&parentID=40460&highlight=ext4)

for windows :

plzz download ext2fds.exe 0.50.....from sourceforge.net...


thnx 2 all.....i have my data back

---

### Post by Rubi1200 on 2011-04-21
Excellent! I am really pleased you were able to rescue your data.

Good luck :)

---

### Post by ishuA on 2011-04-21
i think my file system is repaired ....i am pasting the output of command u asked me 2 use.....plzzz provide me a solution for dual boot
> 

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4dev
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x504ae195

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    64,514,047    64,307,200   7 HPFS/NTFS
/dev/sda3          64,514,048   310,274,047   245,760,000   7 HPFS/NTFS
/dev/sda4         310,276,094   494,069,759   183,793,666   f W95 Ext d (LBA)
/dev/sda5         397,389,824   413,990,911    16,601,088  82 Linux swap / Solaris
/dev/sda6         413,992,960   494,069,759    80,076,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C2461793461786F7                       ntfs       System Reserved               
/dev/sda2        46B61DC7B61DB87F                       ntfs       Windows7                      
/dev/sda3        CE96ECE496ECCDD1                       ntfs       Entertainment                 
/dev/sda5        9d114869-bed7-462e-ae89-3a2a6f8e246c   swap                                     
/dev/sda6        4c1183e7-1f26-46b5-9f67-82b256fc96ed   ext4dev                                  

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=31f1571f,xino=/mnt/live/memory/.aufs.xino,nowarn_perm)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)
/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda3        /mnt/sda3                fuseblk    (rw,noatime,allow_other,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
insmod tga
if background_image /usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.tga ; then
  set color_normal=black/black
  set color_highlight=red/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4c1183e7-1f26-46b5-9f67-82b256fc96ed ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4c1183e7-1f26-46b5-9f67-82b256fc96ed ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 4c1183e7-1f26-46b5-9f67-82b256fc96ed
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c2461793461786f7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4c1183e7-1f26-46b5-9f67-82b256fc96ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d114869-bed7-462e-ae89-3a2a6f8e246c none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 216.6GB: boot/grub/core.img
 214.9GB: boot/grub/grub.cfg
 221.0GB: boot/initrd.img-2.6.35-25-generic-pae
 216.6GB: boot/vmlinuz-2.6.35-25-generic-pae
 221.0GB: initrd.img
 216.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 40  31 05 00 50 fd 00 00 fe  |.......@1..P....|
000001d0  ff ff 05 fe ff ff 02 90  2e 06 00 e8 c5 04 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file



---

### Post by Rubi1200 on 2011-04-21
You need to somehow get the Ubuntu CD working again because you cannot install GRUB2 from Slax.

I suggest you download and burn to CD a new image.

Check the integrity and then burn at the lowest possible speed:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ishuA on 2011-04-21
m not xactly sure about the version of ubuntu i was using ....i.e whether it was a beta or alpha vrsn.....i have another cd of ubuntu 10.10(beta version)....will it work..???

or i can arrange for the same image but it will take some time.....
by the time u can give me the code and i will update u as soon as i get my problems resolved ...
thnx rubi...

---

### Post by Rubi1200 on 2011-04-21
It looks like you have Ubuntu 10.10 installed according to the script results, so the CD you have should work if you can boot the computer with it.

Once you are on the LiveCD, these are the commands you need to run:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Once finished, reboot taking out the CD.

When you are, hopefully, back in Ubuntu, run this command to add the Windows install to the menu:

```
sudo update-grub
```

Let me know how it works out.

---

