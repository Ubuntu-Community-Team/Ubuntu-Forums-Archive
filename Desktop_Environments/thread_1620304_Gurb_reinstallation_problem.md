---
title: "Gurb reinstallation problem"
date: 2010-11-12
forum: Desktop Environments
---

### Post by rotate2010 on 2010-11-12
hello frnds,i am using ubuntu 9.10 lucid version...and also installed windows7 in laptop..now yest i reinstall windows7 again in laptop...so grub was overwritten by mbr...i tried to reinstall grub but i failed by that method which i used to reinstall it when i used ubuntu9.04...is there different method to reinstall grub in ubuntu9.10??if yes pls tell me the solution....so that i can get both os in grub...:):)

---

### Post by garvinrick4 on 2010-11-12
Go to this web  site and download the script to DESKTOP and then run the code below in a  terminal and it will put a file named RESULTS on your desktop. Copy and  paste it to your thread (after copy and paste highlight and click on  the # sign in upper right of message box.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
     

     ```
 sudo bash ~/Desktop/boot_info_script*.sh
```A lot or users have the ability to read this file now and help you. 
Boot problems are not usually a difficult item to repair. PS 9.10 is karmic, 10.04 is lucid
                                                                                               __________________

---

### Post by rotate2010 on 2010-11-20
sorry for late reply...i got busy in other thing...first thnx for ur reply and help..i did whatever u said..but after getting RESULT.txt u said copy and paste it in my thread...so here i am doing same...pls now help me...


  ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   168,185,855   167,774,208   7 HPFS/NTFS
/dev/sda3         168,187,902   594,198,527   426,010,626   f W95 Ext d (LBA)
/dev/sda5         168,187,904   348,563,455   180,375,552   7 HPFS/NTFS
/dev/sda6         348,565,504   528,941,055   180,375,552   7 HPFS/NTFS
/dev/sda7         528,943,104   594,198,527    65,255,424  83 Linux
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        42D8E5C1D8E5B2F9                       ntfs                                     
/dev/sda2        1A82E48D82E46F27                       ntfs       Windows7                      
/dev/sda3: PTTYPE="dos" 
/dev/sda4        F6FA7784FA774043                       ntfs       LENOVO_PART                   
/dev/sda5        A040D1BB40D197FC                       ntfs       Entertaiment                  
/dev/sda6        68ECEE3FECEE0762                       ntfs       Backup and Data               
/dev/sda7        9d70e013-92a0-452c-9876-d15f60163613   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/Backup and Data   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9d70e013-92a0-452c-9876-d15f60163613 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9d70e013-92a0-452c-9876-d15f60163613
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 761219351218fc35
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set f6fa7784fa774043
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1

=================== sda7: Location of files loaded by Grub: ===================


 275.3GB: boot/grub/core.img
 292.7GB: boot/grub/grub.cfg
 275.6GB: boot/initrd.img-2.6.32-21-generic
 279.4GB: boot/initrd.img-2.6.32-24-generic
 279.4GB: boot/initrd.img-2.6.32-25-generic
 275.2GB: boot/vmlinuz-2.6.32-21-generic
 276.3GB: boot/vmlinuz-2.6.32-24-generic
 276.3GB: boot/vmlinuz-2.6.32-25-generic
 279.4GB: initrd.img
 279.4GB: initrd.img.old
 276.3GB: vmlinuz
 276.3GB: vmlinuz.old
```

---

