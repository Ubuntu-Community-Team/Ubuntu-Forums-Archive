---
title: "grub problem can't boot Ubuntu"
date: 2011-04-16
forum: Desktop Environments
---

### Post by adimopoulos on 2011-04-16
Hi to all 

I have my hard drive divided in two partition sda1 and sda2. Ubuntu is always in sda1 and i try different distributions on sda2. Usually i have no problem but ow i have installed Chakra linux on sda2 and can't boot on my Ubuntu anymore. Here is my fdisk -I output  

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043ad9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   531606914   265802433+  83  Linux
/dev/sda2   *   531607552   951031807   209712128   83  Linux
/dev/sda3       951031808   976773119    12870656   82  Linux swap / Solaris

```

and here is the /boot/grub/menu.lst now on my Chakra Linux (it uses grub not grub2).

```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
#
#-*


# (1) Windows
 
hiddenmenu
default 0
timeout 1
 
# (0) Chakra GNU/Linux
title Chakra GNU/Linux
root (hd0,1)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/86f8ed0e-7420-481d-8cc9-74ca08454dfd root=/dev/disk/by-uuid/401769de-eb2e-4f92-b0f4-6aebf1cf34a1 ro
initrd /boot/kernel26.img
 
# (1) Chakra GNU/Linux Fallback
title Chakra GNU/Linux Fallback
root (hd0,1)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/86f8ed0e-7420-481d-8cc9-74ca08454dfd root=/dev/disk/by-uuid/401769de-eb2e-4f92-b0f4-6aebf1cf34a1 ro
initrd /boot/kernel26-fallback.img

# (2) ubuntu 
title Ubuntu 10.10
 root (hd0,0)
 kernel     /boot/vmlinuz-2.6.35-27-generic  
 initrd  /boot/initrd.img-2.6.35-27-generic 

```

I have added the third ((2) Ubuntu) option but didn't help a lot.
hope someone can help 

thanks
Aris

---

### Post by LostinSpacetime on 2011-04-16
I would just install and reconfigure grub2 from the ubuntu live cd. I'm pretty sure it will fix everything :).

---

### Post by varunendra on 2011-04-16
> **LostinSpacetime said:**
> I would just install and reconfigure grub2 from the ubuntu live cd. I'm pretty sure it will fix everything :).
+1

For how to, follow this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

As soon as grub2 is reinstalled (on sda, not sda1 or sda2) it will detect the new OS in sda2 automatically with ```
sudo update grub
```

If reinstalling / updating grub2 couldn't fix it (highly unlikely though) then please post the output of [boot_info_script]("http://bootinfoscript.sourceforge.net/"), using it as described on the linked page.

---

### Post by oldfred on 2011-04-16
I have to agree with the two above posts, that grub2 would be a lot better.

Your old grub legacy entry is not complete. But it may not work anyway as not all grub legacy versions will boot ext4.

title    Most Current Ubuntu on sda1
root    (hd0,0)
linux   /vmlinuz root=/dev/sda1 ro quiet splash
initrd  /initrd.img

---

### Post by telovin on 2011-04-16
Hi Adimopoulos,
Follow the link given in post 3. In that the folllowing steps worked for me.

Boot into Your Ubuntu Live CD. Go to applications- accessories-terminal.

Mount the partition containing the Ubuntu installation.
```
sudo mount /dev/sdXY /mnt
```

Here "XY" can be replaced by  a1 or a2 or b1 or wherevr your Ubuntu partition is. If your Ubuntu partition is on sda1, then the command would be

 ```
sudo mount /dev/sda1 
```

Make sure it is mounted on your desktop.(When it was not seen on my desktop, it did not work for me.It may be different for everyone.)

Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

```
sudo grub-install --root-directory=/mnt /dev/sdX
Here 'X' is sda or sdb wherever your Ubuntu is.

If it is on sda then the command is
sudo grub-install --root-directory=/mnt /dev/sda
```



Reboot from hard disk. Login to Ubuntu If You can see your grub.
Refresh the GRUB 2 menu  by going to applications-accessories-terminal```
sudo update-grub
```

If still not working, then grub experts will help You. The above method worked for me.

---

### Post by adimopoulos on 2011-04-16
Thanks for all the answers but now i'm starting to worry. I have done  what all previous posts mention and i end up with a black screen when  reboot. I cant really figure out what has gone wrong there since  everything seems like straight forward.

So i have mounted sda1 (where ubuntu is)  on /mnt  and then install grub  using the command
```

*sudo grub-install --root-directory=/mnt /dev/sda*

```but then couldn't reboot, the only think i get is the black screen. Now  i'm again on the live CD and my fdisk -l gives again that the boot  partition is sda2 which is weird. 
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043ad9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       33091   265802433+  83  Linux
/dev/sda2   *       33092       59199   209712128   83  Linux
/dev/sda3           59199       60802    12870656   82  Linux swap / Solaris


```
Any advice welcome.

Aris

---

### Post by oldfred on 2011-04-16
Post full boot script. If you hold down shift key from BIOS until grub menu appears, do you get menu. If so this may not tell much.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by adimopoulos on 2011-04-17
Thanks for your time. Done what you asked here is the RESULT.txt

```

ubuntu@ubuntu:~$ cat /home/ubuntu/Downloads/RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
 Chakra Linux (2011.04 - 
                       Aida) () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   531,606,914   531,604,867  83 Linux
/dev/sda2    *    531,607,552   951,031,807   419,424,256  83 Linux
/dev/sda3         951,031,808   976,773,119    25,741,312  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        bf2bd7cd-be70-4ad7-bc1f-3948946be87c   ext4                                     
/dev/sda2        401769de-eb2e-4f92-b0f4-6aebf1cf34a1   ext4                                     
/dev/sda3        86f8ed0e-7420-481d-8cc9-74ca08454dfd   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bf2bd7cd-be70-4ad7-bc1f-3948946be87c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 91208bcf-7b23-4c05-9268-3e06d17330f5
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=91208bcf-7b23-4c05-9268-3e06d17330f5 ro splash quiet
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 91208bcf-7b23-4c05-9268-3e06d17330f5
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=91208bcf-7b23-4c05-9268-3e06d17330f5 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bf2bd7cd-be70-4ad7-bc1f-3948946be87c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cd805f0c-9653-4fff-b897-b7e0f106d81e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 128.9GB: boot/grub/core.img
 146.8GB: boot/grub/grub.cfg
  37.5GB: boot/initrd.img-2.6.32-25-generic
  14.6GB: boot/initrd.img-2.6.35-24-generic
 156.0GB: boot/initrd.img-2.6.35-27-generic
 157.2GB: boot/initrd.img-2.6.35-28-generic
 129.2GB: boot/vmlinuz-2.6.32-25-generic
 129.4GB: boot/vmlinuz-2.6.35-24-generic
 129.8GB: boot/vmlinuz-2.6.35-27-generic
 157.1GB: boot/vmlinuz-2.6.35-28-generic
 157.2GB: initrd.img
 156.0GB: initrd.img.old
 157.1GB: vmlinuz
 129.8GB: vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
#
#-*


# (1) Windows
 
hiddenmenu
default 0
timeout 1
 
# (0) Chakra GNU/Linux
title Chakra GNU/Linux
root (hd0,1)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/86f8ed0e-7420-481d-8cc9-74ca08454dfd root=/dev/disk/by-uuid/401769de-eb2e-4f92-b0f4-6aebf1cf34a1 ro
initrd /boot/kernel26.img
 
# (1) Chakra GNU/Linux Fallback
title Chakra GNU/Linux Fallback
root (hd0,1)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/86f8ed0e-7420-481d-8cc9-74ca08454dfd root=/dev/disk/by-uuid/401769de-eb2e-4f92-b0f4-6aebf1cf34a1 ro
initrd /boot/kernel26-fallback.img

# (2) ubuntu 
title Ubuntu 10.10
 root (hd0,0)
 kernel     /boot/vmlinuz-2.6.35-27-generic  
 initrd  /boot/initrd.img-2.6.35-27-generic 

=============================== sda2/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0


# Commented out by Dropbox
# UUID=401769de-eb2e-4f92-b0f4-6aebf1cf34a1 / ext4 defaults 0 0
UUID=86f8ed0e-7420-481d-8cc9-74ca08454dfd swap swap defaults 0 0
UUID=401769de-eb2e-4f92-b0f4-6aebf1cf34a1 / ext4 defaults,user_xattr 0 0

=================== sda2: Location of files loaded by Grub: ===================


 313.1GB: boot/grub/core.img
 384.0GB: boot/grub/menu.lst
 313.1GB: boot/grub/stage2
 272.9GB: boot/kernel26-fallback.img
 272.8GB: boot/kernel26.img
 313.1GB: boot/vmlinuz26
ubuntu@ubuntu:~$ 

```Hope this will help. 

Aris

---

### Post by oldfred on 2011-04-17
If you hold down shift from BIOS until menu appears, do you get menu?

I would remove quiet splash to see what errors may be posted as you boot.


I do see this but I did not think it would prevent booting, the UUID in fstab does not match:
Actual UUIDs:
/dev/sda3        86f8ed0e-7420-481d-8cc9-74ca08454dfd   swap   

fstab in sda1:
# swap was on /dev/sda5 during installation
UUID=cd805f0c-9653-4fff-b897-b7e0f106d81e none            swap    sw              0       0

You must have created a new swap as part of your install. So now Ubuntu is trying to use the old swap. Edit fstab in sda1 to have correct UUID  the 86f8.... one.

---

### Post by adimopoulos on 2011-04-17
This last post did it. Thanks for the help. I now have both chakra and ubuntu.

Thanks again
Aris

---

### Post by amerinde on 2011-04-17
what happens if u just change boot from 2 back to 1

---

### Post by oldfred on 2011-04-17
@adimopoulos
Glad you got it working.

@   	amerinde
If you mean to move boot flag from sda2 to sda1, that makes no difference. Grub does not use boot flag.

Windows and lilo use boot flag to know which partition to jump to. More boot code is in the partition boot sector - PBR.

Lots of info - applies to all MBR(msdos) systems:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

