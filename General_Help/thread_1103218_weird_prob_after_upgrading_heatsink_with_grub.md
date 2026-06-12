---
title: "weird prob after upgrading heatsink with grub"
date: 2009-03-22
forum: General Help
---

### Post by petemga on 2009-03-22
I replaced my heatsink wiht a new one and when I put my rig back to gether I got a grub 21 error. I fixed the grub error with the super grub cd and am able to boot into ubuntu. When I tried to boot into windows XP I started getting the ntldr is missing error. I replaced the ntldr, boot.ini and ntdetect.com files and now get the system32\hal.dll file is missing or corrupt error. I replaced that and still get the error. I have 3 HDD the first one (C: ) has windows, the 2nd one has Ubuntu and the 3rd one is for storage. I think that problem is that the storage drive with no OS on it is set to the active drive and I cannot change it to C:. C: needs to be the active drive in order for this work correct? I went into the disk management windows utility and it wont let me change the C: drive to the active drive. Does anyone know how to solve this problem?

---

### Post by Bucky Ball on 2009-03-22
Try going into the BIOS when you boot the machine. You may have to hit 'delete' or F1 to get there, before grub. Change the boot order of your drives in there, hit F10 to save and exit and your machine will re-boot and if that is the problem, all should be well.

---

### Post by petemga on 2009-03-22
I tried that and even thouth the Bios recognizes all my drives the C: drive is not listed in the boot order selection.

---

### Post by Bucky Ball on 2009-03-22
Try unplugging all the drives but the one you are trying to boot from. Then add the rest one by one. Labourious but pretty sure fire. That way, if the boot drive doen't boot, you can fix that problem in isolation then work your way through. If it appears, that is. Even if it doesn't, there's a start! No chance it may have died?

* Incidentally, the C drive, as such, is probably a partition on drive sda1, therefore, you want to boot the correct *drive*, not partition. Set it to the correct *drive*, then that will boot from the partition that is set to 'boot'. If you know the boot partition is on the only Western Digital drive in the box, for instance, set that as the first boot device. :)

---

### Post by meierfra. on 2009-03-22
> system32\hal.dll file is missing or corrupt error.

This usually means that you boot.ini is pointing to the wrong partition.  Please post your boot.ini and the output of

```
sudo fdisk -lu
```

---

### Post by petemga on 2009-03-22
Ok, I unhooked the other 2 drives that weret the C: drive and when I did this I got the grub 21 error again. Remember C: has windows, then I have another drive with ununtu and one more for storage. The C: drive is less than a yr old and I am able to boot into it with the simple NTLDR cd from here -> [http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

@meierfra below is a copy of the boot.ini I copied of the disk from the link above.

[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows

[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS seleccione esto primero" /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\Windows="2ND TRY THIS essayez ceci en deuzieme" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect
multi(0)disk(0)rdisk(1)partition(2)\Windows="4TH TRY THIS selezioni questo fourth" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\Windows="5TH TRY THIS selecione este fifth" /fastdetect
multi(0)disk(0)rdisk(1)partition(3)\Windows="6TH TRY THIS seleccione este sexto" /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\Windows="7TH TRY THIS essayez ceci en septieme" /fastdetect
multi(0)disk(0)rdisk(1)partition(4)\Windows="8TH TRY THIS wahlen Sie dieses achte" /fastdetect
C:\="9TH TRY THIS selezioni questo nono"
D:\="10TH TRY THIS selecione este decimo"

---

### Post by meierfra. on 2009-03-22
>  I am able to boot into it with the simple NTLDR cd from here
Good. That means there is nothing wrong with XP.


About the boot.ini you posted. Is that the same  boot.ini  you were using when you got the "system32\hal.dll file is missing" message.  Did you get the error message  directly after you chose "XP"  at the Grub menu. Or did the XP boot menu appear and you got the error message after choosing  one of the items on the XP boot menu.?

Which of the entries  let you boot into XP, when you used the NTLDR cd?

How about plugging all your drives back in, boot  into Ubuntu and   download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by petemga on 2009-03-22
> About the boot.ini you posted. Is that the same boot.ini you were using when you got the "system32\hal.dll file is missing" message. Did you get the error message directly after you chose "XP" at the Grub menu. Or did the XP boot menu appear and you got the error message after choosing one of the items on the XP boot menu.?

When I do not havde the ntldr cd in and i get to the dual boot menu to choose XP or ubuntu, I choose XP and get the error. I plugged all my drives back in and shortly after got my first BSOD since I built this computer. 

Im about to boot into ubuntu and go to sourceforge now. Will post back shortly.

---

### Post by petemga on 2009-03-22
this is my first time using linux and dont know how to install or use .sh (boot_info_script28.sh) files. sorry, but I am a total noob to linux.

---

### Post by meierfra. on 2009-03-22
Did you download the script to the desktop?

Then just open a terminal (Applications->Accessories->Terminal) and type

```
sudo bash ~/Desktop/boot_info_script*.sh 
```
and press "enter"
It will ask you for your password.  While you type the password, it will seem like nothing is happing. That's normal. Just finish typing the password and "press" enter.

---

### Post by petemga on 2009-03-22
```
============================ Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 27358695.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d937d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8be46ad9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5c4b7f4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    13,671,314    13,671,252  83 Linux
/dev/sdc2          27,358,695   948,959,549   921,600,855   7 HPFS/NTFS
/dev/sdc3          13,671,315    27,358,694    13,687,380   f W95 Ext d (LBA)
/dev/sdc5          13,671,378    27,358,694    13,687,317  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ECC0A1E8C0A1B96A" TYPE="ntfs" 
/dev/sdb1: UUID="2220A7DC20A7B4E7" TYPE="ntfs" 
/dev/sdc1: UUID="b02a8dfd-a4ab-49f0-9404-7cf58f3152d2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="01C9A44732D9AF10" TYPE="ntfs" 
/dev/sdc5: UUID="3d7e9012-9f66-44d8-8d33-9de78432d9d7" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pete/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pete)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdc5/boot/grub/menu.lst: ===========================

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
default		0

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
# kopt=root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d7e9012-9f66-44d8-8d33-9de78432d9d7

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


   8.6GB: boot/grub/menu.lst
   8.5GB: boot/grub/stage2
   8.6GB: boot/initrd.img-2.6.27-11-generic
   8.5GB: boot/initrd.img-2.6.27-7-generic
   8.5GB: boot/vmlinuz-2.6.27-11-generic
   8.5GB: boot/vmlinuz-2.6.27-7-generic
   8.6GB: initrd.img
   8.5GB: initrd.img.old
   8.5GB: vmlinuz
   8.5GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-03-22
Could it be that your are booting from the storage  drive?


Try this. Open a terminal and then open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Add the following  to the very end of the file:

title		Microsoft Windows XP Home Edition (hd1)
root		(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1


title		Microsoft Windows XP Home Edition (hd2)
root		(hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader	+1


Save the file and reboot.
Try both new entries on the Grub menu. If one of them works, you can delete all the others from menu.lst.

If none of them works, report all error messages you got.

---

### Post by petemga on 2009-03-22
im my menu I now have two more xp options. Windows XP home hd 1 and windows XP home hd 2. when I select the first i get the hal.dll error again and on the 2nd I get error 13: Invalid or unsupported executable format. press any key to continue...

1. If I formatted the disk with ubuntu on it would it fix this issue?
2. I dont understand why in the disk management utility in windows it shows the 3rd HD (the storage drive) as the active drive and wont let me change the active drive to C: (HD 1)

---

### Post by meierfra. on 2009-03-23
>  if I  formatted the disk with ubuntu on it would it fix this issue?

No. You still will get error 21.


It's getting late for me. Let my quickly  show you how  to be able to boot into XP and Ubuntu, by switching the boot order in the bios. And tomorrow I write up instruction how add Ubuntu to the XP boot loader:

Open a terminal in Ubuntu.

```
sudo grub 
```
and at the "grub>" prompt:

```
root (hd2,4)
setup (hd2)
quit
```

Then

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
```

Reboot. If  you set your bios to boot from the XP drive you should boot directly into XP.

If you set your bios to boot from the Ubuntu drive, you should get the Grub menu. (And maybe a miracle occurs and one of the Windows entries actually works)

---

### Post by petemga on 2009-03-23
I didnt switch anything in the BIOS and it booted right into XP!! Thanks. Now all we have to do is get back to where I can dual boot and we will he set. You are awesome. 

One more thing though. I have no sound in XP but do have sound in Ubuntu. Weird...oh well, talk to you tomorrow and thanks again!

PS before I forget, do you have any idea why this happened and if I have to make some harware changes in the future and un-hook my drives will it happen again?

---

### Post by Bucky Ball on 2009-03-23
It's a good idea to back up and re-install after hardware changed on the board. What exactly do you mean by heatsink? Do you mean the CPU fan? That shouldn't have caused any of this unless you took the CPU out to do it, which probably would have been unavoidable.

---

### Post by petemga on 2009-03-23
Yes, it was a heatsink CPU fan (Zalman 9500) because I have overclocked the CPU. I took out the motherboard and unhooked everything, but did not remove the CPU from the mobo. Its a good idea to reinstall with a major hardware chanfe like a CPU or motherboard, but you shouldnt have to reinstall after a CPU fan upgrade should you?

Also, I was wondering if marked the partition that has Ubuntu on it as active in the Disk Management utitlity in windows, would I see it in my grub screen, becuase now it just boots straight into windows.

---

### Post by meierfra. on 2009-03-23
Set your bios to boot from the Ubuntu drive and boot.  Then you should get the Grub Menu.

See whether you can boot into Ubuntu. 
Also try out all the Windows item on the Grub Menu. If one of them works,  just deleted all other  Windows entries from menu.lst and you are all set.

But I doubt that any of the Windows item will works. So here are the instructions how to add Ubuntu to the XP boot menu. **(Only do this if you were not able to boot into XP from the Grub menu)**

Boot into Ubuntu and open a terminal


**Step 1**  Install Grub to the boot sector of the Ubuntu partition.

```
sudo grub
```
and at the "Grub>" prompt:

```

device (hd2) /dev/sdc
device (hd0) /dev/sdc
root   (hd2,4)
setup (hd0,4)
quit

```

** Step 2 ** Edit menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

Change 

"timeout 10" to "timeout 3"

and

"#hiddenmenu" to "hiddenmenu"


** Step 3**  Copy the Ubuntu boot sector to a file in the Windows partition.

```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sdc5 of=/mnt/ubuntu.bin count=1

```

By very careful with the "dd" command. It's best to copy and paste the command rather than retype it. If "dd" runs for more than just a couple of seconds, use "Ctrl+C" to stop it.


** Step 4**  Edit boot ini.
```
 sudo nano /mnt/boot.ini
```
add this line to the end the file:

C:\ubuntu.bin="Ubuntu"

To save the  file press

```
"Ctrl+X"
"Y"
"Enter"

```

That's it.
Reboot, but set your bios  to boot from the XP drive. You should get  the XP boot menu, which lets you choose between XP and Ubuntu.

---

### Post by petemga on 2009-03-23
in the boot priority menu in the BIOS i dont see my drive with linux in it as an option to set to boot from. when I check the disk manager utility in XP the linux drive is not set to active, but the storage drive (drive 3) is.

---

### Post by meierfra. on 2009-03-23
OK.  Boot from the SuperGrubDisk and choose

!Linux! (1) AUTO

at the  first screen.

If this boots you into Ubuntu,  carry out the instructions how to add Ubuntu  to XP Boot Menu.

If SuperGrub does not work, boot from the Ubuntu Live CD and then follow the instruction. But skip step 2 (you can carry out step 2 once you booted into Ubuntu from the XP Boot menu)

---

### Post by Slim Odds on 2009-03-23
> **meierfra. said:**
> Good. That means there is nothing wrong with XP.

I'm sorry, but I must give big you a big ole LOL for that one..... :D

---

### Post by petemga on 2009-03-23
when I did that with the super grub disk I got the error 13 again.

---

### Post by meierfra. on 2009-03-23
O.K. Just boot from the Ubuntu  Live CD and follow the instruction to add Ubuntu to the XP boot loader. But skip step 2.

---

### Post by petemga on 2009-03-23
I put the CD in and it wants me to reinstall ubuntu. I skipped the installation and now am running ubuntu from the cd. How do I get it to let me add ubuntu to the boot menu? did I miss something? 

sorry for being a pain in the a$$ but you are really helping me and I appreciate it. This is my first install of any linux distro.

---

### Post by meierfra. on 2009-03-23
> How do I get it to let me add ubuntu to the boot menu? did I miss something? 

Just follow the instruction from post #18. 
So open terminal via Applications->Accessories->Terminal, and then carry out Steps 1,3 and 4 from post 18.

---

### Post by petemga on 2009-03-23
oh OK, duh... :D I will do it when I get back from the store. I have to run out real quick. So, now I will no longer use the grub menu? doesn't that suck? Also, did this happen because I unhooked the motherboard? I didn't take the CPU off the board. Its not going to happen again if I have to unhook my hard drives is it?

---

### Post by mc4man on 2009-03-23
> I have to unhook my hard drives is it
Not as long as you put them back on the same connectors as they were
(assumming in this case sata 0, sata 1, ect.

---

### Post by petemga on 2009-03-23
I did what you said in post 18 and I still dont have an option in the BIOS to boot from the HD with ubuntu on it. All my drives are recognized, but in the boot priority menu I dont see the disk with linux on it as an option to boot from.

If I reformatted the disk with Ubuntu on it, would this fix the problem?

---

### Post by meierfra. on 2009-03-23
Sorry, you don't need to boot from the Ubuntu drive.

What happens when you boot  normally (that is from the XP drive)  You should get a boot  menu where you can choose between XP or Ubuntu.  Or do you boot directly into XP?

If you don't get a boot menu, boot from the LiveCD, download the boot info script, run the script (just as the last time) and post  RESULTS.txt


> If I reformatted the disk with Ubuntu on it, would this fix the problem? 
I doubt it.

---

### Post by petemga on 2009-03-23
i just boot directly into XP. I am going to run the script from the live CD now.

---

### Post by petemga on 2009-03-23
fyi: I found my Ghost 14.0 DOS disk which I had misplaced and reinstalled a clean image of my C: drive. I dont have an image for the linux drive because I had just installed it.

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /bsudo bash ~/Desktop/boot_info_script*.shoot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 27358695.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d937d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8be46ad9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5c4b7f4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    13,671,314    13,671,252  83 Linux
/dev/sdc2          27,358,695   948,959,549   921,600,855   7 HPFS/NTFS
/dev/sdc3          13,671,315    27,358,694    13,687,380   f W95 Ext d (LBA)
/dev/sdc5          13,671,378    27,358,694    13,687,317  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ECC0A1E8C0A1B96A" TYPE="ntfs" 
/dev/sdb1: UUID="2220A7DC20A7B4E7" TYPE="ntfs" 
/dev/sdc1: UUID="b02a8dfd-a4ab-49f0-9404-7cf58f3152d2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="01C9A44732D9AF10" TYPE="ntfs" 
/dev/sdc5: UUID="3d7e9012-9f66-44d8-8d33-9de78432d9d7" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdc5/boot/grub/menu.lst: ===========================

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
default		0

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
# kopt=root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d7e9012-9f66-44d8-8d33-9de78432d9d7

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3d7e9012-9f66-44d8-8d33-9de78432d9d7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Microsoft Windows XP Home Edition (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


title Microsoft Windows XP Home Edition (hd2)
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1



=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=3d7e9012-9f66-44d8-8d33-9de78432d9d7 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


   8.5GB: boot/grub/menu.lst
   8.5GB: boot/grub/stage2
   8.6GB: boot/initrd.img-2.6.27-11-generic
   8.5GB: boot/initrd.img-2.6.27-7-generic
   8.5GB: boot/vmlinuz-2.6.27-11-generic
   8.5GB: boot/vmlinuz-2.6.27-7-generic
   8.6GB: initrd.img
   8.5GB: initrd.img.old
   8.5GB: vmlinuz
   8.5GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-03-23
It seems that none of the Steps from Post 18 actually work. Did you get any error messages?


So I suggest to try again, make sure that you follow the direction precisly.  Don't type the commands yourself. Use Copy and paste instead. (to paste in the terminal use "Ctrl+Shift+V" or choose "paste" in the "edit" menu.)

Boot from the Ubuntu LiveCD and open a terminal


**Step 1** Install Grub to the boot sector of the Ubuntu partition.


```
sudo grub
```

and at the "Grub>" prompt:


```
device (hd2) /dev/sdc
device (hd0) /dev/sdc
root   (hd2,4)
setup (hd0,4)

```

At this point  copy  the whole content of the terminal  and post it here.
(To copy from the terminal:  "Ctrl+Shift+C" or choose "copy" from the "Edit" menu)

```
quit
```



Step 3 Copy the Ubuntu boot sector to a file in the Windows partition.



```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sdc5 of=/mnt/ubuntu.bin count=1
```

By very careful with the "dd" command. It's best to copy and paste the command rather than retype it. If "dd" runs for more than just a couple of seconds, use "Ctrl+C" to stop it.


Step 4 Edit boot ini.

 ```
sudo nano /mnt/boot.ini
```

add this line to the end the file:

C:\ubuntu.bin="Ubuntu"

To save the file press


```

"Ctrl+X"
"Y"
"Enter"
```

```
cat /mnt/boot.ini
```

Copy the whole content of the terminal and post it here.

---

### Post by petemga on 2009-03-23
this is the code from the terminal right before i pasted quit into the teminal.

```
grub> setup (hd0,4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd2,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd0,4) /boot/grub/stage2 p /boot/grub/me
nu.lst "... succeeded
Done.

```

so, from here on out do I copy paste the rest of this stuff from your post into the same terminal? BTW I was using copy and paste the first time i did it. I just must have messed up somewhere.

---

### Post by petemga on 2009-03-23
after I put quit  into the terminal, this is what it says:

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 
```

---

### Post by meierfra. on 2009-03-23
The output you posted seems to be o.k.

>  from here on out do I copy paste the rest of this stuff from your post into the same terminal?

Yes.

---

### Post by meierfra. on 2009-03-23
your second output is fine,too.

---

### Post by petemga on 2009-03-23
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition"$
```

do i add:
add this line to the end the file:

C:\ubuntu.bin="Ubuntu"

To save the file press

...to the above in the terminal?

---

### Post by meierfra. on 2009-03-23
>  	
Re: weird prob after upgrading heatsink with grub
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition"$
```

do i add:
add this line to the end the file:

C:\ubuntu.bin="Ubuntu"

To save the file press

...to the above in the terminal? 


Yes.  You are currently editing the  file "boot.ini".  You just have to add one line to it, namely "C:\ubuntu.bin="Ubuntu".

The rest of the instruction just tell you how to save the file.


(P.S sorry for the delay, I got distracted by  another case, which also needed immediate attention)

---

### Post by meierfra. on 2009-03-23
It seems you finished step 2 and 3. 
You can do Step 4 any time. But  if you rebooted  since you completed step 3, you need to  repeat the "mount" command. So  open "boot.ini" via


```
sudo mount /dev/sda1 /mnt
sudo nano /mnt/boot.ini
```

And then edit and save  the file according to my previous instruction.


But actually if you are no longer on the LiveCD, it will be easier to edit "boot.ini"  from  XP:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by joewski on 2009-03-24
I had a similar problem with a freeNAS system I have.

What I found the problem to be is a bad Fan. It seemed to cause noise (voltage fluctuation) on the hard drive power supply lines causing the harddrives to be underpowered during writes. I had similar problems.
I have 4 hard drives and one DVD drive. When I tested the system with the fan I had only 1 HD and 1 DVD. The worst thing about this hardware problem is everything will boot, work but when you start doing some heavy read writes to disk the system would hang. My culprit was a 3-4" fan. 

Solution

1. Power down your system immediately. (No point in losing more of your data.)

2. Disconnect all your fans that you can, except the CPU fan into the motherboard, the graphics card fan and the powersupply fan(you can't disconnect the power supply fan I know).

3. Do disk checks before rebooting, with whatever tools you have, ie spinwrite, pmagic etc. 

Now if your not doing intensive gaming or graphics work you don't need that many fans going.

---

### Post by petemga on 2009-03-24
i think i got it!!


```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\ubuntu.bin="Ubuntu"

```

---

### Post by petemga on 2009-03-24
it works! i start with the XP dual boot menu and when I choose Ubuntu it takes me to the grub menu where i can then log into Ubuntu. If I choose the first XP choice in the grub menu it will take me back to the XP dual boot menu and if I try one of the other XP choices that we added, I still get the errors, so I will remove those. 

Thank you SOOO much! Now I am going to study up on my linux since this is my first install. ;)

---

### Post by meierfra. on 2009-03-24
> it works! 
Great!.

> I still get the errors, so I will remove those. 
When you do that,  you can  carry out step two at the same time. Then you won't have to go through two boot menus.

---

### Post by petemga on 2009-03-24
i build gaming computers for people and just started taking some college classes on networking, so thought I was pretty computer savvy, but have never tried Linux until two weeks ago and realized how awesome it is. I will eventually take some Linux classes in my line of studies, but was wondering if you could point me in the right direction to start learning about Linux now. 

Thanks!! 

I really do appreciate your help as well!! :KS

---

