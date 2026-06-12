---
title: "/dev/sda2 is no longer the partition where Windows is on"
date: 2010-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by crisco552 on 2010-04-17
I'm not quite sure if this is the right place if I bought a dell with windows then installed ubuntu, but oh well. After getting over my troubles with GRUB's conflicts with Dell Datasafe Local Backup I decide to get rid of the RECOVERY partition. I boot into ubuntu and try to delete it and expand the NTFS windows partition. That doesn't work so I create a new Fat32 partition in place of the recovery partition. now when I try in GRUB to boot into windows it tries to boot into the fat32 partition because it is now labelled /dev/sda2 and the windows partition is /dev/sda3. How can I simply and easily fix this problem with out any reinstallations besides grub?

---

### Post by Kai Summers on 2010-04-18
Hi,
Open up /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```

There should be a section that looks something like this
```
title        Microsoft Windows XP
root        (hd0,2)
makeactive
chainloader    +1
```


Assuming that they are both on the same drive and you just wand to change from sda2 to sda3

change the line 
```
root        (hd0,2)
``` 
to 
```
root      (hd0,3)
```

Hope that helps let us know how you get on.

---

### Post by crisco552 on 2010-04-18
I'm sorry, but there is no menu.lst. but in grub.cfg there is 
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set dc86cccc86cca87a
    chainloader +1

```would I change that?

---

### Post by Kai Summers on 2010-04-18
Sorry I was referring to an older version of grub. Change the following line:
set root=(hd0,2)

to:
set root=(hd0,3)

Don't forget that all these changes need to be performed under sudo. Let us know how you get on.

---

### Post by crisco552 on 2010-04-18
I'm sorry for my obvious lack of language skills, but what exactly do you mean in you last line "Let us know how you get on."? also when I try to save it, it tells me that it is read only and that I can't save.

---

### Post by Kai Summers on 2010-04-18
"Let us know how you get on" - Advise on progress to your problem as to notify site mods that the thread can be marked as solved once your problem is rectified.

When you are opening this file are you opening in terminal using the 'sudo gedit /boot/grub/grub.cfg' command as you will need the right privileges to save the file.

Try as above first - I'm not 100% but you might have to 'chmod u+w /boot/grub/grub.cfg' To give write permission to the file, but once finished change it back by using  'chmod u+r /boot/grub/grub.cfg'.

---

### Post by crisco552 on 2010-04-18
yes I am doing 'sudo gedit /boot/grub/grub.cfg' to open it. here's a screenshot of what it says: [https://dl.dropbox.com/u/5135448/grub.png](https://dl.dropbox.com/u/5135448/grub.png)

---

### Post by Kai Summers on 2010-04-18
OK so you need to assign write permissions to the file and folder run the following commands

sudo chmod u+w /boot/grub/grub.cfg
sudo chmod u+w /boot/grub/

Then try the sudo gedit command

---

### Post by crisco552 on 2010-04-18
thank you. I will now try and see if it work ;)

---

### Post by crisco552 on 2010-04-18
Nope, still didn;t work :'(

Edit: here's the entire grub.cfg file [http://pastie.org/926280](http://pastie.org/926280)

---

### Post by Kai Summers on 2010-04-18
Try sudo update-grub and see if it will detect windows and perform the neccessary changes automatically.

---

### Post by crisco552 on 2010-04-18
nope it didn't I am so mad at myself right now. I should not mess with partitions any more.

---

### Post by Kai Summers on 2010-04-18
Please refer to your private messages.

---

### Post by wilee-nilee on 2010-04-19
Post this boot script, I suspect that the original ms boot was in the recovery.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Do you have a XP install or recovery disc? Also confirm the MS OS.

---

### Post by crisco552 on 2010-04-19
My MS OS is Windows 7 home premium... adn I am probably going to reinstall windows, then just install ubuntu in a vm. I rarely use it anymore anyways.

---

### Post by crisco552 on 2010-04-19
here is what my RESULTS.txt says
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 80325.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb4f8998

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2              80,325    30,796,604    30,716,280   b W95 FAT32
/dev/sda3          30,801,920   320,726,758   289,924,839   7 HPFS/NTFS
/dev/sda4         320,737,725   488,392,064   167,654,340   5 Extended
/dev/sda5         320,737,788   481,468,049   160,730,262  83 Linux
/dev/sda6         481,468,113   488,392,064     6,923,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        9C77-7D9A                              vfat                                     
/dev/sda3        E09ED03F9ED00FC0                       ntfs       OS                            
/dev/sda5        5348463c-c251-4989-be93-aad504c6c547   ext4                                     
/dev/sda6        a4a290c7-b689-45c9-9830-d74f47f48e0e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/9C77-7D9A         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 5348463c-c251-4989-be93-aad504c6c547
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5348463c-c251-4989-be93-aad504c6c547
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=5348463c-c251-4989-be93-aad504c6c547 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5348463c-c251-4989-be93-aad504c6c547
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=5348463c-c251-4989-be93-aad504c6c547 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5348463c-c251-4989-be93-aad504c6c547
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5348463c-c251-4989-be93-aad504c6c547 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5348463c-c251-4989-be93-aad504c6c547
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5348463c-c251-4989-be93-aad504c6c547 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5348463c-c251-4989-be93-aad504c6c547 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a4a290c7-b689-45c9-9830-d74f47f48e0e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 164.5GB: boot/grub/core.img
 167.5GB: boot/grub/grub.cfg
 164.7GB: boot/initrd.img-2.6.31-14-generic
 165.1GB: boot/initrd.img-2.6.31-20-generic
 164.7GB: boot/vmlinuz-2.6.31-14-generic
 164.8GB: boot/vmlinuz-2.6.31-20-generic
 165.1GB: initrd.img
 164.7GB: initrd.img.old
 164.8GB: vmlinuz
 164.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by wilee-nilee on 2010-04-19
> **crisco552 said:**
> My MS OS is Windows 7 home premium... adn I am probably going to reinstall windows, then just install ubuntu in a vm. I rarely use it anymore anyways.

I am not a expert on the boot script stuff, but it is helpful for the people who are. If you have nothing to lose then a fresh install and a virtual seems like the easiest/quickest answer. I think what you have is fixable, but it might just take a while to do it as far as getting help.

The W7 forums are very good you might want to at least have them as a bookmark.
[http://www.sevenforums.com/](http://www.sevenforums.com/)
There are lots of instructional threads there, even one for installing the boot stuff into the main W7 partition if a person wants to remove the 100mb boot partition created when W7 is a fresh install. This thread on there may be part of the answer, in that grub is still looking at the original recovery partition.

---

### Post by crisco552 on 2010-04-19
I think I might just do that. but if it would be possible to fix this in a somewhat short amount of time (like 2days) then I would rather do that because of all the programs I'd have to redownload (that's the only reason. I have all my data backed up on a external hd)

---

