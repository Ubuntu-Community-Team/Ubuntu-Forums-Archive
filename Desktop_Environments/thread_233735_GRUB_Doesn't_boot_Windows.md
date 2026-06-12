---
title: "GRUB Doesn't boot Windows"
date: 2006-08-10
forum: Desktop Environments
---

### Post by lorothrigs on 2006-08-10
When I select Microsoft Windows XP Professional from the GRUB boot list I get:

> root		(hd0,0)
	"Filesystem unknown, partition type 0x7"
savedefault
makeactive
chainloader	+1

Is there anyway to fix this?

---

### Post by Tomosaur on 2006-08-10
Paste the results of 'sudo fdisk -lu' please (run it in a terminal).

And also the contents of /boot/grub/menu.lst

---

### Post by lorothrigs on 2006-08-10
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   113290379    56645158+   7  HPFS/NTFS
/dev/hda2       113290380   154529234    20619427+  83  Linux
/dev/hda3       154529235   156360644      915705    5  Extended
/dev/hda5       154529298   156360644      915673+  82  Linux swap / Solaris

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+   0  Empty
/dev/sda2          160650    58074974    28957162+   b  W95 FAT32
/dev/sda3        58074975    58605119      265072+  83  Linux
Partition 3 does not end on cylinder boundary.

---

### Post by Tomosaur on 2006-08-10
Try altering the word 'root' for 'rootnoverify'.

---

### Post by lorothrigs on 2006-08-10
Alright, I tried that and now it just says
> Booting 'Microsoft Windows XP Professional'

rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Tomosaur on 2006-08-10
Very odd :S

I can't think of why this would be happening to you, sorry. Maybe someone else will have an answer. Have you tried reinstalling grub?

---

### Post by lorothrigs on 2006-08-10
How do you go about reinstalling grub?

---

### Post by Tomosaur on 2006-08-10
There's a thread about it on here somewhere, use the seach box on the top right.

---

### Post by lorothrigs on 2006-08-12
This is my menu.lst

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
rootnoverify            (hd0,0)
savedefault
makeactive

```

---

### Post by seshomaru samma on 2006-08-12
I had a similar problem on a Fedora/XP box. It turned out it was a Windows problems. I put in the Windows Cd and ran 
```
fixmbr
```
this killed grub but allowed XP to boot.
then I reinstalled Grub by booting the Ubuntu Live CD
Choose the first option (something like 'start or install Ubuntu')
Then I opened a terminal and ran these two commands :
```
sudo grub
find /boot/grub/stage1
```
I put the output of the second command here (replace the question marks with the output):
```
root (hd?,?)
```
(in my case it was hd0,1)
and then these two commands:
```
setup (hd0)
quit
```
hope this helps

---

### Post by lorothrigs on 2006-08-12
I tried fixmbr but that completely ****** over my XP install, it just went black with colored squares in like 3 spots...

---

### Post by Illusionistx on 2006-08-13
i think this is the same situation i'm having, only everytime i select xp from GRUB it just reloads GRUB. hopefully tomorrow i'll try fixmbr

---

### Post by seshomaru samma on 2006-08-13
> **lorothrigs said:**
> I tried fixmbr but that completely ****** over my XP install, it just went black with colored squares in like 3 spots...

It is unlikely that fixmbr will destroy your XP install because it doesn't deal with XP at all, just the bootloader. If fixmbr didn't work , I suspect your XP problem is more serious than just a bootloader.

---

### Post by lorothrigs on 2006-08-13
No, no. When I typed "fixmbr" after the BIOS screen the screen was just black with a few colored squares...before I installed GRUb it worked just fine.

---

### Post by seshomaru samma on 2006-08-13
> **lorothrigs said:**
> No, no. When I typed "fixmbr" after the BIOS screen the screen was just black with a few colored squares...before I installed GRUb it worked just fine.

Did you boot with Windows CD?
You need to access the restoration mode or whatever they call it
After you boot from XP CD , you will get 3 options , one is resoration or something similar - you chose it with the letter R
Then it will ask you for your admin password and will give you a terminal
In that terminal you put :
```
fixmbr
```
if this doesn't work it means you have some problem with your Windows or that you didn't choose the right partition (I think Windows CD asks you which partition you want to access as admin , but i might be wrong here...)

---

### Post by lorothrigs on 2006-08-13
That is exactly what I did. Twice.

---

### Post by Tomosaur on 2006-08-13
Isn't there another option on the recovery CD which says something like 'FIXBOOT' or anything? It's been a while since I used the recovery CD, but I seem to remember some option with 'boot' in the title.

Anyway, if the FIXMBR was indeed successful, then it does sound like Windows is corrupt in general.

---

### Post by lorothrigs on 2006-08-13
I just decided to backup my data onto the Linux partition, and format the WinXP partition, then reinstall WinXP. Thanks for your help :)

---

### Post by duff on 2006-08-22
I'm having the same problem on a new computer as well.  **rootnoverify** didn't work, neither did **fixmbr**.  Then I came across this:

[http://en.opensuse.org/SDB%3AWindows_No_Longer_Boots_Following_the_Installation_of_SUSE_LINUX_9.1](http://en.opensuse.org/SDB%3AWindows_No_Longer_Boots_Following_the_Installation_of_SUSE_LINUX_9.1)

It appears the SUSE devs have found and fixed the problem, since that bug report says it's fixed after 9.1.

I was going to try to use the fix listed in that report, but it requires the SUSE 9.1 install CD, which I can't find on [their server](http://download.opensuse.org/distribution/).  Anybody know how to do this in Ubuntu?

---

