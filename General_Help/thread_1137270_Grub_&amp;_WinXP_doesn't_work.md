---
title: "Grub &amp; WinXP doesn't work"
date: 2009-04-25
forum: General Help
---

### Post by Wrbhhh on 2009-04-25
Hi...

I can't boot Windows XP with Grub. I googled and searched this forum, but I didn't find anybody with the same problem I have.

When I select WinXP form the boot list, a message is displayed saying "Starting up ..." but nothing happens. I have to restart the computer.

I have 2 hard disks, an IDE and a SATA. Kubuntu 9.04 (upgraded from 8.10) is installed on IDE and XP on SATA. Grub is in the MBR of the IDE disk and Windows bootloader is on SATA.

I've had the same problem a few years ago on Dapper Drake too. I didn't get it to work.

XP is on (hd1,0) and Kubuntu is on (hd0,5).

If I change the hard disk priority in BIOS, Grub is bypassed and XP loads normally.

I even tried booting from Grub CLI by typing in commands, but the result is always the same.

_**fidsk -l:**_
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb615e73c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2222       14946   102213531    7  HPFS/NTFS
/dev/sda2               2        2221    17832150    f  W95 Ext'd (LBA)
/dev/sda5               2         263     2104483+  82  Linux swap / Solaris
/dev/sda6             264        2221    15727603+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122f122e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sdb2            1959       30401   228468397+   7  HPFS/NTFS
```

_**/boot/grub/device.map:**_
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

_**/boot/grub/menu.lst**_
```
default saved
timeout 5
failsafe 0 1
color yellow/green blink-light-blue/green

### BEGIN AUTOMAGIC KERNELS LIST
## <CUT>

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.27-14-generic
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro quiet splash
initrd /boot/initrd.img-2.6.27-14-generic
savedefault

title Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro  single
initrd /boot/initrd.img-2.6.27-14-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
chainloader +1
#savedefault
savedefault 0
makeactive
#hide (hd0,0)
#hide (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)

```

I tried with these *hide* options too. It didn't help. If you need more info, just say so...

---

### Post by meierfra. on 2009-04-25
The entry you are using should work. So let's have  a close look at your system to figure out was is causing your problems: 

 Boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by Wrbhhh on 2009-04-25
Ok, here are the results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb615e73c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     35,680,428   240,107,489   204,427,062   7 HPFS/NTFS
/dev/sda2              16,065    35,680,364    35,664,300   f W95 Ext d (LBA)
/dev/sda5              16,128     4,225,094     4,208,967  82 Linux swap / Solaris
/dev/sda6           4,225,158    35,680,364    31,455,207  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x122f122e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,455,269    31,455,207   7 HPFS/NTFS
/dev/sdb2          31,455,270   488,392,064   456,936,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="32287EF7287EBA05" TYPE="ntfs" 
/dev/sda5: UUID="6ebda66b-fff5-49f0-9b52-c4898ee74edf" TYPE="swap" 
/dev/sda6: UUID="1b3a29d5-8448-49fa-a17e-fc8d10a26e91" TYPE="ext2" 
/dev/sdb1: UUID="2870C45B70C430FC" TYPE="ntfs" 
/dev/sdb2: UUID="FCF06C6DF06C3056" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /sdb2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


=========================== sda6/boot/grub/menu.lst: ===========================

default saved
fallback 0
timeout 5
color yellow/green blink-light-blue/green

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b3a29d5-8448-49fa-a17e-fc8d10a26e91

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.27-14-generic
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro quiet splash
initrd /boot/initrd.img-2.6.27-14-generic
savedefault

title Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro  single
initrd /boot/initrd.img-2.6.27-14-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
savedefault 0
#hide (hd1,1)
#hide (hd0,0)
#unhide (hd1,0)
root (hd1,0)
makeactive
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=32287EF7287EBA05 /sda1           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=2870C45B70C430FC /sdb1           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=FCF06C6DF06C3056 /sdb2           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=6ebda66b-fff5-49f0-9b52-c4898ee74edf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  14.4GB: boot/grub/menu.lst
  14.4GB: boot/grub/stage2
  14.4GB: boot/initrd.img-2.6.27-14-generic
  14.4GB: boot/initrd.img-2.6.28-11-generic
  14.4GB: boot/vmlinuz-2.6.27-14-generic
  14.4GB: boot/vmlinuz-2.6.28-11-generic
  14.4GB: initrd.img
  14.4GB: initrd.img.old
  14.4GB: vmlinuz
  14.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200



```

---

### Post by meierfra. on 2009-04-25
Add all of these  to menu.lst

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


title Microsoft Windows XP Professional (no map)
rootnoverify (hd1,0)
chainloader +1

title Microsoft Windows XP Professional (hd0)
rootnoverify (hd0)
map (hd1) (hd0)
chainloader +1

title Microsoft Windows XP Professional (hd1)
rootnoverify (hd1)
map (hd1) (hd0)
chainloader +1


Try them all. If none of them works, and report any error messages you got.

---

### Post by Wrbhhh on 2009-04-26
I've tried all of them and the result is always the same. The message "Starting up ..." and that's it. It just stays that way. I have to restart the computer via the restart button.

---

### Post by zeex on 2009-04-26
Hi, 

I can't tell you why it isn't working but i do have the same setup you have. 2 hard disk one with ubuntu and other with XP. I did this for my own convenience. I switch HDD priority in BIOS to choose the OS i want. not a very good way to go but it works for me. 

Something I have noticed. I don't know if it's true but it's my own observation. The windows should be installed in the first partition linux can be installed in any partition. Once i installed linux in first partition and windows on 3rd partition of same disk. I faced the same situation you 've right now. I have no idea why cuz people say it worked for 'em. Now you 've windows on second HDD. Windows has issues with it's boot loader, frankly it sucks.

I gave up and now i change HDD priority to use Linux/windows.

---

### Post by Wrbhhh on 2009-04-26
Yeah, MS (once again) did a lousy job with their bootloader.

For now I'm booting XP the same way, by changing the hard disk order. But this isn't a good solution because this is a home computer and others are using it too. As they have almost no computer knowledge, it's a bit complicated for them to change the hard disk order. This is much simpler. A menu appears and they select XP.

---

### Post by zeex on 2009-04-26
Hi, 

I looked into your menu.lst. You should map the disk before chainloder and makeactive. 

You have XP on (hd0,0) , ubuntu on (hd0,5)

You have an an entry in you menu.lst

> title Microsoft Windows XP Professional
rootnoverify (hd1,0)
chainloader +1
#savedefault
savedefault 0
makeactive
#hide (hd0,0)
#hide (hd1,1)
map (hd0) (hd1)         
map (hd1) (hd0)


you are mapping after chainloader and makeactive. This will not work.

Replace this with 

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1


This should work if don't require any special driver to access your drives.

---

### Post by Wrbhhh on 2009-04-26
> **zeex said:**
> You have XP on (hd0,0) , ubuntu on (hd0,5)

XP is on (hd1,0). :confused:

> **zeex said:**
> Replace this with 

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1

I tried it and it didn't work also. Again the same. In fact, I think these were the default options (which also didn't work).


> **zeex said:**
> This should work if don't require any special driver to access your drives.

Yes, I've seen this in the grub manual. How can I check this? And if this is the case, can I change it (and how)? The XP disk is SATA so it's possible it has some non-default SATA drivers. :?:

---

### Post by zeex on 2009-04-26
Hi,

I tried this on my PC it's working fine. Thanks to your post now i don't 've switch HDD priority everytime wanna switch OS.

The only difference i see between our setup is that I have 2 IDE drives and you have 1 IDE and 1 SATA. I don't have SATA so i can't say anything about it but I'll explain how I did it in my system. 

My 2 IDE drives are connected to Primary IDE channel. Disk1 say (hd0) is Master drive and has linux+grub installed in it. Disk2 say (hd1) is slave drive with windows XP and it's bootloader installed.

Disk1 (hd0) Linux Master_drive
Disk2 (hd1) Windows Slave_drive

From fdisk -l I got windows installed in (hd1,0)


I added these lines to /boot/grub/menu.lst

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

I'll explain the commands. For windows to boot it should be on the primary disk. Map command virtually switches the primary and secondary disks

map (hd0) (hd1)     // mapping primary disk hd0 to secondary hd1
map (hd1) (hd0)     // mapping secondary disk hd1 to primary hd0

After these commands now the slave drive with windows XP is the primary drive. rootnoverify (hd1,0) points to the windows and rest is self explanatory i guess.

I made a mistake in my earlier post. I wrote 
> title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)    **// here replace (hd0,0) with (hd1,0)**
makeactive
chainloader +1

It should be 

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Try this , just replace that one line. It should work.

Good luck :)

---

### Post by Wrbhhh on 2009-04-26
> **zeex said:**
> Try this , just replace that one line. It should work.

And again it didn't work. :(

---

### Post by zeex on 2009-04-26
> **Wrbhhh said:**
> And again it didn't work. :(

i don't understand why is it not working for you. May be because of SATA and IDE drives. It worked on first trial in my system.

I think it's because of the driver requirement of SATA but i don't know how to check whether your hardware needs special drivers

Sorry :| ... do post the reason though when you get it done.

---

### Post by zeex on 2009-04-26
Hi, 

I'm still searching :) I found this you may try.

title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

I got this in ubuntu forum may 2007 posts. [http://ubuntuforums.org/archive/index.php/t-430450.html]("http://ubuntuforums.org/archive/index.php/t-430450.html")

Let me know if this works :) cuz this is actually for two SATA disks.

---

### Post by Wrbhhh on 2009-04-26
I've tried this before and it didn't work. I've also tried it now and again, it didn't work. :(

Thanx for trying...

---

### Post by meierfra. on 2009-04-26
Seems to be one of the rare cases where grub is not able to chain load XP.  So I suggest to add Ubuntu to the Windows boot loader:


**Step 1 **Install Grub to the boot sector of the Ubuntu Partition:


```
sudo grub
```

and at the grub prompt:

```

device (hd0) /dev/sda
device (hd1) /dev/sda
root (hd1,5)
setup (hd0,5)
quit

```

**Step 2** Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sdb1 /mnt
sudo dd if=/dev/sda6 of=/mnt/ubuntu.bin bs=512 count=1
```
By  very careful with the "dd" command. If it runs for more than just a couple of seconds, stop the process with "Ctrl+C".

**Step 3** Edit boot.ini:

```
sudo nano /mnt/boot.ini
```

(Remark:  Do not use "gedit" in place of "nano": gedit  does not handle "dos" file very well)

Add this to the end of the file (start a new line, but do not leave a blank line):

C:\ubuntu.bin="Ubuntu"

Save the file.


Reboot and set your bios to boot from the Window drive.
You should get the XP boot menu where you can choose between XP and Ubuntu.


If you are able to boot into XP and Ubuntu, you should edit your menu.lst so that you don't have to go through two  menus.

Just change

"timeout 10" to "timeout 2"

and

"#hiddenmenu" to "hiddenmenu".

---

### Post by Wrbhhh on 2009-04-26
Thanx for your help. I'll give it a try. Could you just take one more look at your post, just to be sure there's no typo. Thanx once again. I'll report my progress.

> **meierfra. said:**
> ```
sudo grub
```
```

device (hd0) /dev/sda
devide (hd1) /dev/sda
root (hd1,5)
setup (hd0,5)
quit

```
```
sudo mount /dev/sdb1 /mnt
sudo dd if=/dev/sda6 of=/mnt/ubuntu.bin bs=512 count=1
```
```
sudo nano /mnt/boot.ini
```

---

### Post by meierfra. on 2009-04-26
Darn, I had doubled check everything. But there still was a typo

```
devi[COLOR="Red"]d[/COLOR]e (hd1) /dev/sda
```

is supposed to be 


```
devi[COLOR="Red"]c[/COLOR]e (hd1) /dev/sda

```

---

### Post by Wrbhhh on 2009-04-26
I've tried following your steps. I get the Win bootloder menu. Selecting WinXP works as it should. But selecting Ubuntu freezes the computer.

I also got 2 warnings while doing the following command:
```
grub> setup (hd0,5)
```Here they are:
```
Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd1,5)"... failed (this is not fatal)
```

---

### Post by meierfra. on 2009-04-26
> Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd1,5)"... failed (this is not fatal)

That's normal. It always happens when you install grub  to a partition rather than the MBR.

> But selecting Ubuntu freezes the computer.
Could you run the boot info script again?  Make sure to post the new RESULTS.txt (it might be called RESULTS1.txt)

---

### Post by Wrbhhh on 2009-04-26
Here it is:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 28211334 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub0.97 in the file /ubuntu.bin looks at sector 
                       28211334 on boot drive #2 for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #6 for /boot/grub/menu.lst.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb615e73c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     35,680,428   240,107,489   204,427,062   7 HPFS/NTFS
/dev/sda2              16,065    35,680,364    35,664,300   f W95 Ext d (LBA)
/dev/sda5              16,128     4,225,094     4,208,967  82 Linux swap / Solaris
/dev/sda6           4,225,158    35,680,364    31,455,207  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x122f122e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,455,269    31,455,207   7 HPFS/NTFS
/dev/sdb2          31,455,270   488,392,064   456,936,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="32287EF7287EBA05" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="6ebda66b-fff5-49f0-9b52-c4898ee74edf" 
/dev/sda6: UUID="1b3a29d5-8448-49fa-a17e-fc8d10a26e91" TYPE="ext2" 
/dev/sdb1: UUID="2870C45B70C430FC" TYPE="ntfs" 
/dev/sdb2: UUID="FCF06C6DF06C3056" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /sdb2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


=========================== sda6/boot/grub/menu.lst: ===========================

default saved
fallback 0 1
timeout 5
color yellow/green blink-light-blue/green

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b3a29d5-8448-49fa-a17e-fc8d10a26e91

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.27-14-generic
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro quiet splash
initrd /boot/initrd.img-2.6.27-14-generic
savedefault

title Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 ro  single
initrd /boot/initrd.img-2.6.27-14-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional (old)
savedefault 0
#hide (hd1,1)
#hide (hd0,0)
#unhide (hd1,0)
root (hd1,0)
makeactive
map (hd1,0) (hd0,5)
map (hd0,5) (hd1,0)
chainloader +1

title Microsoft Windows XP Professional (bleh)
root (hd1,0)
makeactive
#map (hd0) (hd1)
#map (hd1) (hd0)
chainloader +1
savedefault 0

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1b3a29d5-8448-49fa-a17e-fc8d10a26e91 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=32287EF7287EBA05 /sda1           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=2870C45B70C430FC /sdb1           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=FCF06C6DF06C3056 /sdb2           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=6ebda66b-fff5-49f0-9b52-c4898ee74edf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  14.4GB: boot/grub/menu.lst
  14.4GB: boot/grub/stage2
  14.4GB: boot/initrd.img-2.6.27-14-generic
  14.4GB: boot/initrd.img-2.6.28-11-generic
  14.4GB: boot/vmlinuz-2.6.27-14-generic
  14.4GB: boot/vmlinuz-2.6.28-11-generic
  14.4GB: initrd.img
  14.4GB: initrd.img.old
  14.4GB: vmlinuz
  14.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ubuntu.bin="Ubuntu"

```

---

### Post by dougalkerr on 2009-04-26
It certainly sounds like the Windows boot manager has screwed up. I had a similar problem about a year ago when I was dual booting with Ubuntu and Vista. 
Donwload and burn SuperGrub to a cd and start the machine with this disc in place. Make sure your PC can start from a CD by checking this option in your BIOS.
Once you get SuperGrub loaded just follow the options and see what happens. Try the option for loading !Win! it should fix Windows boot manager.
This will (or should) start Windows for you.
If it does you can reboot the PC and opt for one of the dual booting options and you should have a working boot loader again.

---

### Post by meierfra. on 2009-04-26
Strange. Everything is configured correctly.  Maybe your bios are only able to handle one hard drive at the time.

Try this. Boot from the Ubuntu drive. At the grub menu press "c". Type

```
geometry (hd0)
geometry (hd1)
geometry (hd2)

```

This should list the partitions on all  of your  hard drives. Are both hard drives detected?

---

### Post by Wrbhhh on 2009-04-26
> **dougalkerr said:**
> It certainly sounds like the Windows boot manager has screwed up. I had a similar problem about a year ago when I was dual booting with Ubuntu and Vista. 
Donwload and burn SuperGrub to a cd and start the machine with this disc in place. Make sure your PC can start from a CD by checking this option in your BIOS.
Once you get SuperGrub loaded just follow the options and see what happens. Try the option for loading !Win! it should fix Windows boot manager.
This will (or should) start Windows for you.
If it does you can reboot the PC and opt for one of the dual booting options and you should have a working boot loader again.

Actually, I've already downloaded Super Grub. I needed it when I hid the linux partition (which contains grub) so grub couldn't load. I needed Super grub to unhide the linux partition. I'll try this tomorrow.

> **meierfra. said:**
> Strange. Everything is configured correctly.  Maybe your bios are only able to handle one hard drive at the time.

Try this. Boot from the Ubuntu drive. At the grub menu press "c". Type

```
geometry (hd0)
geometry (hd1)
geometry (hd2)

```This should list the partitions on all  of your  hard drives. Are both hard drives detected?

Everything looks ok. Just one thing, for NTFS partition it says "Filesystem type unknown". I don't know if that's ok...

---

### Post by meierfra. on 2009-04-26
> for NTFS partition it says "Filesystem type unknown". I don't know if that's ok...
That's normal. Grub cannot read "ntfs" partitions.


Sorry, I just have no clue what the problem could be.

But since the problem was caused by upgrading from 8.10 to 9.04,  it seems that its grub fault. Lets see what happens if  you reinstall grub 

```
sudo apt-get purge grub
sudo  apt-get install grub
sudo grub-install --recheck /dev/sda

```

Also repeat Steps 1 and Step 2 from post 15.

Then try booting from each of your two drives and see how far you get.

---

### Post by Wrbhhh on 2009-04-26
> **meierfra. said:**
> But since the problem was caused by upgrading from 8.10 to 9.04,  it seems that its grub fault. Lets see what happens if  you reinstall grub 

Sorry if I wasn't clear enough. The problem wasn't caused by upgrading Ubuntu. The problem was present on 8.10 too and even when i had Dapper Drake (when Dapper Drake was the newest distro). It was all on the same computer.

I'll try these suggestions tomorrow. Thanx.

---

### Post by meierfra. on 2009-04-26
> The problem was present on 8.10
That makes more sense. 
Then I think that the problems is caused by some kind of  weird interaction between grub and your bios.

> I'll try these suggestions tomorrow. 
Actually, now that I know that the problems was not cause by upgrading, there is virtually no chance that reinstalling grub with help.

I'll think about the problem  and  will let you know what to try next.

---

### Post by zeex on 2009-04-27
> **meierfra. said:**
> 

**Step 1 **Install Grub to the boot sector of the Ubuntu Partition:


```
sudo grub
```

and at the grub prompt:

```

device (hd0) /dev/sda
device (hd1) /dev/sda
root (hd1,5)
setup (hd0,5)
quit

```



Hi,

I'm been following this post. mapping device worked for me. I 've 2 IDE drives. But i'm still trying to unerstand why is it not working for Wrbhhh.

I read about modifying windows bootloader to boot linux but i don't understand some of your steps, more specifically what i've quoted. I understood the dd command and the rest of it.

You used /dev/sda in both *device *commands and you used (hd1,5) for root and (hd0,5) for setup. why?

Could you please explain why this step was needed ?

---

### Post by meierfra. on 2009-04-27
**Wrbhhh:** You problem might be caused by some setting in your bios.  
I have seen a case where changing from "RAID" mode to "ACHI" cured the "Starting Up" error. 

So have a look at your bios and see whether  you can find any settings  which could make a difference. Change only one setting at a time. Make sure to record the original settings.

---

### Post by meierfra. on 2009-04-27
> You used /dev/sda in both device commands and you used (hd1,5) for root and (hd0,5) for setup. why?

Could you please explain why this step was needed ?

Sure.  Usually one would install grub to the boot sector  of the Ubuntu partition with the command

root (hd0,5)
setup (hd0,5)


The boot sector of the ubuntu partition will now contain instructions to look for stage 2 on partition 6 of the current hard drive. Now the boot sector is copied to file on  the Windows partition.   If one  tries boot from that file, the code  in that file  will look   for stage2 on partition 6 of the current hard drive. But the current hard drive is the Windows drive (/dev/sdb) But stage 2 is on the Ubuntu drive (/dev/sda).

So one has to find a way to install grub to boot sector of the Ubuntu partition, so that the same boot code is suitable for booting from a file in the Windows  partition.

Lets examine

device (hd0) /dev/sda
device (hd1) /dev/sdb
root (hd1,5) 
setup (hd0,5)

The first line tells the grub-shell  that in in the following (hd0)  refers to /dev/sda
The second  line tells the grub-shell   that (hd1)   refers to /dev/sda

root (hd1,5) tells the grub-shell that the stage files and menu.lst are on partition 6 of  (hd1) (and so on partition 6 of /dev/sda).

setup (hd0,5) tells  the grub-shell to install stage1 of grub to the boot sector of the partition 6 of (hd0) (and so to the boot sector of partition 6 of /dev/sda).

Since "root (hd1,5)" told grub that stage2 is on (hd1),  the boot sector of partition 6 of /dev/sda  now contains instructions to look for stage 2 on partition 6 of the second hard drive. (recall here that grub starts counting at zero)

This boot sector is copied to a file on the window partition. The code in this file will look for stage 2 on partition 6 of the second hard drive.
This is indeed  the correct location of the stage 2 files: During boot up, the windows drive is the first hard drive (since that's boot drive) and Ubuntu is the second  hard drive.

---

### Post by Wrbhhh on 2009-04-28
> **meierfra. said:**
> **Wrbhhh:** You problem might be caused by some setting in your bios.  
I have seen a case where changing from "RAID" mode to "ACHI" cured the "Starting Up" error. 

So have a look at your bios and see whether  you can find any settings  which could make a difference. Change only one setting at a time. Make sure to record the original settings.

I didn't find anything like that in BIOS. The only thing I found was that I could turn RAID on and put SATA disks in a RAID array. But by default it was turned off.

Would a BIOS upgrade help?

---

### Post by meierfra. on 2009-04-28
```
The only thing I found was that I could turn RAID on
```
Try that, but don't  put the SATA drives in an array.

> Would a BIOS upgrade help? 
It might help, but I'm not sure.  In some rare case BIOS upgrades can cause serious harm. Given that you  have a fully functional computer and are only trying to make booting more convenient, I don't recommend upgrading your bios.

If turning on "RAID" does not help, I suggest to give Grub4Dos a try:

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

### Post by Wrbhhh on 2009-04-28
> **meierfra. said:**
> ```
The only thing I found was that I could turn RAID on
```Try that, put don't  put the SATA drives in an array.

It didn't help.

> **meierfra. said:**
> If turning on "RAID" does not help, I suggest to give Grub4Dos a try:

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

And again it didn't work. It freezes when I select "Start Grub". I'm pretty mad right now. I've really hoped this would work. I just can't understand why it doesn't. If only there were some kind of boot debugger...

Well, thanx for all your help. I guess that's it...

---

### Post by meierfra. on 2009-04-28
> I guess that's it...

Well, there is one more thing  you can try. It's a little bit of work, but I'm pretty sure that it will succeed:   Create a 200MB boot partition for Ubuntu on the Windows drive (/dev/sdb)

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by Wrbhhh on 2009-04-29
> **meierfra. said:**
> Well, there is one more thing  you can try. It's a little bit of work, but I'm pretty sure that it will succeed:   Create a 200MB boot partition for Ubuntu on the Windows drive (/dev/sdb)

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

I could try this. But I have to defragment my NTFS partitions first. So this will have to wait until I have some more time. I'll report here when I get it done.

Thanx for all your help.

---

### Post by Barba Pere on 2009-05-07
I have the same situation:
 - 1st disk is usually (was) SATA, but right now it is PATA.
SATA has xp on first partition, and PATA has kubuntu 9.04.

Right now first one is PATA disk which has GRUB, and SATA disk has win xp MBR on the beginning

Everithing works just fine in my case. I can boot XP and KUbuntu 9.04 from GRUB on PATA disk

Here is my menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a510db59-58ae-49ef-bb38-a2d31ef7079b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1
savedefault
makeactive



```


and here is my report from that file RESULTS.txt

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf843f843

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   390,716,864   288,318,555   f W95 Ext d (LBA)
/dev/sda5         102,398,373   390,716,864   288,318,492   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63f62cb1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   f W95 Ext d (LBA)
/dev/sdb5          81,995,823   184,008,509   102,012,687   7 HPFS/NTFS
/dev/sdb6         184,008,573   286,438,949   102,430,377   7 HPFS/NTFS
/dev/sdb7         286,439,013   390,716,864   104,277,852   7 HPFS/NTFS
/dev/sdb8                 189     3,903,794     3,903,606  82 Linux swap / Solaris
/dev/sdb9           3,903,858    81,995,759    78,091,902  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7ABC5E65BC5E1C47" TYPE="ntfs" 
/dev/sda5: UUID="1624594824592C4D" LABEL="Backup" TYPE="ntfs" 
/dev/sdb5: UUID="01C9897E23E1B950" TYPE="ntfs" 
/dev/sdb6: UUID="01C9897E2A409550" TYPE="ntfs" 
/dev/sdb7: UUID="01C9897E2C2E0D70" TYPE="ntfs" 
/dev/sdb8: TYPE="swap" UUID="becd3554-bc9a-4304-bd4a-1cf1f0bbb21c" 
/dev/sdb9: UUID="a510db59-58ae-49ef-bb38-a2d31ef7079b" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb9 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb9/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a510db59-58ae-49ef-bb38-a2d31ef7079b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a510db59-58ae-49ef-bb38-a2d31ef7079b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify	(hd0,0)
chainloader	+1
savedefault
makeactive



=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb9 during installation
UUID=a510db59-58ae-49ef-bb38-a2d31ef7079b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=becd3554-bc9a-4304-bd4a-1cf1f0bbb21c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb9: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/menu.lst
   3.3GB: boot/grub/stage2
   2.9GB: boot/initrd.img-2.6.28-11-generic
   2.8GB: boot/vmlinuz-2.6.28-11-generic
   2.9GB: initrd.img
   2.8GB: vmlinuz

```

IT works just fine in my case. hope it helps

---

### Post by Wrbhhh on 2009-11-01
Well... The new version (9.10) came out. With it came a new version of grub which solved the problem. I don't know what's changed in this new version of grub, but the problem disappeared.

---

