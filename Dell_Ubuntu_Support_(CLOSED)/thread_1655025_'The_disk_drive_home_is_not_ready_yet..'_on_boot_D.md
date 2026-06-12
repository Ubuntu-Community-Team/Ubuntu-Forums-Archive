---
title: "'The disk drive /home is not ready yet..' on boot Dell N5010"
date: 2010-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eklavya_18 on 2010-12-29
HI,
I have Ubuntu **10.10** on my Dell Inspiron **N5010** ([click here]("http://www.dell.com/us/p/inspiron-15r/pd") for specs) with **no dual boot**.

I have been getting disk errors but after disc check on every boot Ubuntu would boot fine. But since yesterday
I get this message on boot " *The disk drive /home is not ready yet or not present. Continue to wait, S to skip mounting, M for Manual recovery* "

In fstab, I have /home identified by '/dev/sda6' and not by UUID.
I have / and /home on different partitions as follows
/sda
 /sda1    /              ext4
 /sda4   extended
  /sda6  /home       ext4
  /sda7                  ntfs

1) If I **skip** then I get login screen. After logging in I get '/home/abhishek/.ICEAuthority' error message and **nothing but blank desktop** appears. Probably because /home is not mounted and '/home/abhishek/.nautilus' is not found.

2) If I go for **Manual Recovery** :
 **'ls /dev' does not show /dev/sda6**. Though /dev/sda4 is there.
 If I try to mount /dev/sda6 on /home then i get error message " special device /dev/sda6 does not exist'. I cant mount even after doing
#MAKEDEV sda
 because then it says the '/dev/sda5 is not a valid block device'.

I know above two problems are common and there are solutions for them on Internet. But things are not working for me. I am Stuck. Please help.
Thnx

---

### Post by ajgreeny on 2010-12-29
Can you copy back here the output of either ```
fdisk -l
``` from recovery mode, or ```
sudo fdisk -l
``` from a live CD. That will tell us the details of your partition setup, and may show where your /etc/fstab is incorrect.

The partition numbering is a bit unusual, unless you have deleted partitions in the past, which may be affecting the device naming in the /etc/fstab file, hence the current default use of UUIDs in fstab to avoid device naming going astray in such circumstances.

It seems possible that there may be a hardware disk fault, but let's go one step at a time.

---

### Post by eklavya_18 on 2010-12-29
Hey thnx for reply :)
Ya I had deleted some partitions in the past.
Today, I ran LiveCD through usb. Following command dint work
```
sudo fdisk -l 
Unable to read /dev/sda
```But, all the partitions were mounted and I could browse through all the files through the LiveCD. Even " sudo blkid " is giving UUID for /home (/dev/sda6) partition. Following is output of /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=/dev/sda1  /              ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=/dev/sda6 /home           ext4    errors=remount-ro 0       2
# swap was on /dev/sda7 during installation
UUID=60acf072-d740-4501-b3ea-32694fbf33ac none         swap    sw              0       0

```Shall I put UUIDs instead of device names in fstab?

---

### Post by ajgreeny on 2010-12-29
You already have UUIDs in fstab.  The lines starting with # are commented out and notm read by the system at boot, but are there for clarification purposes.  However, if you have messed about with partitions, and perhaps reformatted some of them or added space to existing partitions, some of the naming may have changed.

My biggest worry is that the fdisk command did not show any output, so I am wondering what is going on;  I don't think I have ever seen that before.

---

### Post by gbrainin on 2010-12-29
You need to put _either_ UUIDs or device names.  What you have is a hybrid, which I don't think should work.  For example, the line:```
UUID=/dev/sda6 /home           ext4    errors=remount-ro 0       2
```
Should read either:```
UUID={long alphanumeric string} /home           ext4    errors=remount-ro 0       2
```
Or```
/dev/sda6 /home           ext4    errors=remount-ro 0       2
```

---

### Post by eklavya_18 on 2010-12-30
Hey thnx ajgreeny and gbrainin,

I changed the entries in fstab to alphanumerics and the system booted fine. It was a big relief. But, still my concern is that on every boot my disks are checked for errors and fixed. Is it due to corrupted hard disk?

---

### Post by gbrainin on 2010-12-30
It seems you have two, possibly related problems: first, that it checks the disk on every boot, and second, that it finds and (allegedly) fixes errors every time.  Regarding the first problem, I'm wondering what the setting for number of boots between file checks is.

What is the output of this command?:```
sudo dumpe2fs -h /dev/sda6 | grep -i 'mount count'
```

---

### Post by ajgreeny on 2010-12-30
Whoops!

I had not noticed the lines that began with **UUID=/dev/sda1**, and **UUID=/dev/sda6** and I agree that it would not work, but just confuse the whole system.

If you can not stop the file system check happening after a boot-up check is carried out, in spite of the mount count being set properly, it may be worth doing the operation from a live CD with the command ```
sudo e2fsck /dev/sda1
``` and then ```
sudo e2fsck /dev/sda6
```which can sometimes do a better job than the boot time check.

---

### Post by eklavya_18 on 2010-12-31
Every time I turn on my laptop I have to run LiveCD and check my disks. Thereafter, it boots fine.

Following is the output of
```
sudo dumpe2fs -h /dev/sda6 | grep -i 'mount count'
[sudo] password for abhishek: 
dumpe2fs 1.41.12 (17-May-2010)
Mount count:              2
Maximum mount count:      25

```

Any idea what's happening here?

---

### Post by gbrainin on 2010-12-31
So far, no.  I would suggest trying ajgreeny's idea: start the system up from a live CD and run the e2fsck commands suggested.

---

### Post by mopplow on 2011-04-03
Has anyone found a way to fix this without booting form the live cd every time?
I've found that when I boot from my live USB (I'm using Ubuntu 10.10 on an acer aspire one d-255 netbook, so I cannot use an actual cd), my entire hard drive is under /dev/sd**b**(number) while when I don't have the live USB in, everything is under /dev/sd**a**(number). I don't know if this has anything to do with it.
I've put only UUID's in /etc/fstab , and it still doesn't seem to want to work without the live USB

---

### Post by drs305 on 2011-04-03
> **mopplow said:**
> 
I've put only UUID's in /etc/fstab , and it still doesn't seem to want to work without the live USB

You will have to be a bit more specific about what is happening. If it just doesn't want to boot at all, do you have Grub installed to your hard drive. If it was installed only to the USB it wouldn't boot without it.

If this is what is happening, you can easily fix it from a running system with:
```
sudo grub-install /dev/sdX
```
Substitute the correct drive for "sdX", and do NOT include the partition number.

---

### Post by mopplow on 2011-04-03
I do have Grub installed and running fine.
I'm having the same problem as the original poster; Ubuntu will boot but it tells me *the disk drive /home is not ready yet or not present*
In my /etc/fstab file I have every one of my drives identified by the correct UUID's. I just don't understand why it is not working correctly when it seems like everything is exactly the way it should be

---

### Post by drs305 on 2011-04-03
> **mopplow said:**
> I do have Grub installed and running fine.
I'm having the same problem as the original poster; Ubuntu will boot but it tells me *the disk drive /home is not ready yet or not present*
In my /etc/fstab file I have every one of my drives identified by the correct UUID's. I just don't understand why it is not working correctly when it seems like everything is exactly the way it should be

Even though it may not be a Grub problem, posting the contents of the boot info script may provide some insight. It gives us fstab, UUIDs etc, which we could ask for separately but just running the script might be almost as easy and more comprehensive:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mopplow on 2011-04-03
What results would help from the boot info script? I've downloaded and run it and the file seems too long for me to post the entire thing here.

---

### Post by drs305 on 2011-04-03
> **mopplow said:**
> What results would help from the boot info script? I've downloaded and run it and the file seems too long for me to post the entire thing here.

It is a long file, and indeed there are large parts we won't need. But the easiest thing to do is copy it to a new post, hightlight it all (CTRL-a), then press the # icon in the post's menubar. That will put it inside 'code' tags which will limit the content to a fixed-size window.

---

### Post by mopplow on 2011-04-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     7,831,551     7,831,520   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    23,070,719    23,068,672  12 Compaq diagnostics
/dev/sdb2    *     23,070,720   234,255,243   211,184,524   7 HPFS/NTFS
/dev/sdb3         234,256,382   312,580,095    78,323,714   5 Extended
/dev/sdb5         234,256,384   265,914,367    31,657,984  83 Linux
/dev/sdb6         309,276,672   312,580,095     3,303,424  82 Linux swap / Solaris
/dev/sdb7         265,916,416   309,274,623    43,358,208  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1CFD-0B34                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DA8A19B68A198FDD                       ntfs       PQSERVICE                     
/dev/sdb2        905082A75082941E                       ntfs       ACER                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        cb0e2112-6a96-4a77-9e76-7b6da729def0   ext4                                     
/dev/sdb6        87a4a62f-b4ba-454c-aa2d-d88bdf0a77ab   swap                                     
/dev/sdb7        1963e7db-797f-46ab-aa9e-fc4c12983d03   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb7        /media/1963e7db-797f-46ab-aa9e-fc4c12983d03 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/cb0e2112-6a96-4a77-9e76-7b6da729def0 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb0e2112-6a96-4a77-9e76-7b6da729def0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb0e2112-6a96-4a77-9e76-7b6da729def0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cb0e2112-6a96-4a77-9e76-7b6da729def0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set da8a19b68a198fdd
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 905082a75082941e
    drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=cb0e2112-6a96-4a77-9e76-7b6da729def0 /               ext4    errors=remount-ro 0       1
UUID=1693e7ab-797f-46ab-aa9e-fc4c12983d03 /home           ext4    nodev,nosuid      0       2
# swap was on /dev/sdb6 during installation
UUID=87a4a62f-b4ba-454c-aa2d-d88bdf0a77ab none            swap    sw              0       0


=================== sdb5: Location of files loaded by Grub: ===================


 133.0GB: boot/grub/core.img
 122.2GB: boot/grub/grub.cfg
 122.6GB: boot/initrd.img-2.6.35-22-generic
 133.0GB: boot/vmlinuz-2.6.35-22-generic
 122.6GB: initrd.img
 133.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 7f 77 00 85 3b 00 00  00 00 00 00 02 00 00 00  |..w..;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 34 0b fd 1c 4e  4f 20 4e 41 4d 45 20 20  |..)4...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 2e  77 00 00 66 ba 00 00 00  |..E}.f..w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2011-04-03
:D

I think it was worth posting. In the blkid results, the /home UUID starts with "1963", but in fstab you have it starting with "1693".

That's your problem. (I didn't check the entire alphanumeric, so paste the entire string to be sure.)

---

### Post by mopplow on 2011-04-03
I've fixed that and it still doesn't work :/ would a fresh install be the easiest way to fix this? I've had everything backed up so it wouldn't be a big deal at all

---

### Post by drs305 on 2011-04-03
> **mopplow said:**
> I've fixed that and it still doesn't work :/ would a fresh install be the easiest way to fix this? I've had everything backed up so it wouldn't be a big deal at all

I have to log off and can't reinspect your posted results at the moment. It is often faster to reinstall that to continue to troubleshoot problems. 

In this case, since the UUID was incorrect there may be something else that is easily correctable. On the other side, if you already have good backups and haven't made extensive customizations it may be easier to reinstall if you really can't determine the cause and don't think it would be repeated. 

I'll check back tomorrow. If you aren't in a rush you can let others read and offer opinions.

---

