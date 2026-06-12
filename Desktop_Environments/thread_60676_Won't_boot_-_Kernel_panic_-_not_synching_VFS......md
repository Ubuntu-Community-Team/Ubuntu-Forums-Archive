---
title: "Won't boot - Kernel panic - not synching: VFS....."
date: 2005-08-28
forum: Desktop Environments
---

### Post by filemanager on 2005-08-28
When trying to boot up, right after the "decompressing Linux" part, I get this error:

> 
Kernel panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)


Also, when I go into the GRUB menu and press "e" to edit the boot command line thing, here's what it says in there:

> 
root (hd0,4)
kernel /vmlinuz root=/dev/hda6 ro console=tty0 quiet splash
initrd /initrd.img
savedefault
boot


I don't know what that means or how to fix it =\ Last time I shut down my computer normally, and didn't get any errors. I read there might be a problem in the menu.1st file, but I don't know how to get into it since Linux won't boot.

I have WinXP on one partition, and Linux on another.

Can anyone help so my computer becomes usable again? (WinXP works, but... meh....)

---

### Post by jlacroix on 2005-08-28
Did you just install a new kernel or recompile one?

I did, and I have that same problem. I tried kernels 2.6.12.5 and 2.6.12.4. My problem remains unsolved but I hope yours isn't the same.

Run this command in the terminal: "sudo fdisk -l" and post the output here.

---

### Post by stumpadoodle on 2005-08-29
[QUOTE=filemanager]When trying to boot up, right after the "decompressing Linux" part, I get this error:



Also, when I go into the GRUB menu and press "e" to edit the boot command line thing, here's what it says in there:



I don't know what that means or how to fix it =\ Last time I shut down my computer normally, and didn't get any errors. I read there might be a problem in the menu.1st file, but I don't know how to get into it since Linux won't boot.

I have WinXP on one partition, and Linux on another.

Can anyone help so my computer becomes usable again? (WinXP works, but... meh....)[/QUOTE]


I get that same exact, word for word error on my laptop about 4 out of 5 times i try to boot linux...when it works, it works fine, but other than that, my hard drive was already a bit broken when i started using it. Perhaps there's a section of bad data somewhere on the disk?

---

### Post by filemanager on 2005-08-29
[QUOTE=jlacroix]Did you just install a new kernel or recompile one?

I did, and I have that same problem. I tried kernels 2.6.12.5 and 2.6.12.4. My problem remains unsolved but I hope yours isn't the same.

Run this command in the terminal: "sudo fdisk -l" and post the output here.[/QUOTE]
 I installed Ubuntu back in July, and when I rebooted yesterday it just started saying that.

How do I run that in the terminal when I can't get past that error message? I get the error message even if I try to boot up in "recovery mode" =\

---

### Post by jlacroix on 2005-08-29
I didn't know that you weren't able to get in under recovery mode. Does it let you boot a livecd? If it does, does your livecd read your hard drive okay?

---

### Post by Koba on 2005-08-29
ok, i am having ALMOST the exact same problem, but here is the error i get:
Kernel panic - not syncing: Attempted to kill init!
and thats as far as it gets... thats right after the loading Ubunutu message... can someone please help me?

---

### Post by filemanager on 2005-08-29
I got into my Linux partition using explore2fs, and got into my menu.1st file, here's what it reads:

> 
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro console=tty0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default 
root		(hd0,4)
kernel		/vmlinuz root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default (recovery mode)
root		(hd0,4)
kernel		/vmlinuz root=/dev/hda6 ro console=tty0 single
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,4)
kernel		/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda6 ro console=tty0 single
initrd		/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,4)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# Windows XP

title=Windows XP
rootnoverify (hd0,0)
chainloader +1


Does this help any?

---

### Post by jlacroix on 2005-08-29
It looks fine, except a few of the entries use the same initrd image, but I don't know if that's really a problem or not, (on mine they are all different) I'm not an expert but I'm trying to help regardless. :(

---

### Post by filemanager on 2005-08-29
[QUOTE=jlacroix]I didn't know that you weren't able to get in under recovery mode. Does it let you boot a livecd? If it does, does your livecd read your hard drive okay?[/QUOTE]
 In recovery mode, right before the usual 'not synching' error message I get "Cannot mount "hda6" or unknown block(0,0)"

I'm not sure how to boot off a liveCD, whenever I boot up my computer with the CD in, it just wants to install over the existing installation.

---

### Post by filemanager on 2005-08-29
[QUOTE=jlacroix]It looks fine, except a few of the entries use the same initrd image, but I don't know if that's really a problem or not, (on mine they are all different) I'm not an expert but I'm trying to help regardless. :([/QUOTE]
 Thanks, I do appreciate your help 8)

---

### Post by jlacroix on 2005-08-29
With the ubuntu live cd, you can attempt to mount your root partition, and if it lets you and you can read the files, then we know the partition is fine. However, since explore2fs worked for you, then you pretty much already completed that troubleshooting step so there's no need for the livecd now.

Here is my menu.lst:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.12.4-omega 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12.4-omega root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12.4-omega
savedefault
boot

title		Ubuntu, kernel 2.6.12.4-omega (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12.4-omega root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12.4-omega
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Notice how each kernel entry of mine has a different initrd image. While it may or may not be the problem, I don't like it.

---

### Post by Koba on 2005-08-29
i don't want to redo all my work on my ubuntu, but if there isn't a recover installation on the install disc, then i'm gunna have to unless someone can help us (seems our problems are one and almost the same...)

---

### Post by snpz on 2005-08-29
Wait a minute - take Ubuntu Live CD (not Install CD) and just let it boot up your PC! It will not install something else on your PC.
When u boot up, then try to chek out your HDD! Might be that there are some bad blocks or somethink.
Just a guess!

---

### Post by jlacroix on 2005-08-29
Koba, can you find a way to post your /boot/grub/menu.lst file?

---

### Post by snpz on 2005-08-29
[QUOTE=Koba]i don't want to redo all my work on my ubuntu, but if there isn't a recover installation on the install disc, then i'm gunna have to unless someone can help us (seems our problems are one and almost the same...)[/QUOTE]

U recompiled your kernel before this error message?

---

### Post by filemanager on 2005-08-29
Hmm, looks like you're running x86, while I'm running amd64. I wonder if that makes a difference. shrug.

In my /boot folder in Explore2fs, I only have one initrd image file, so I guess that's the only way they can point ;)

---

### Post by jlacroix on 2005-08-29
I'm not sure but I think that's a bad thing.

---

### Post by filemanager on 2005-08-29
[QUOTE=snpz]Wait a minute - take Ubuntu Live CD (not Install CD) and just let it boot up your PC! It will not install something else on your PC.
When u boot up, then try to chek out your HDD! Might be that there are some bad blocks or somethink.
Just a guess![/QUOTE]
 Hmm *looks around*... I have the x86 Live CD here, but I can't find the AMD64 one. I'll d/l it and burn it to CD tomorrow and try this out. 

I want my Linux (and all my data :P) back! 8\

---

### Post by Koba on 2005-08-29
[QUOTE=jlacroix]Koba, can you find a way to post your /boot/grub/menu.lst file?[/QUOTE]
 how would i get the menu.1st file? i do have win xp (running right now) but how would i get to the file? as soon as i get to it i'll post it, but i have no clue how to :\
snpz, no, i haven't recompiled my kernel, i recently installed the kubuntu-desktop on my ubuntu, but it was loading fine before (with kubuntu-desktop installed) it all of a sudden came up with this message...

---

### Post by filemanager on 2005-08-29
Koba: Looks like this guy is having the exact same problem as you (same error message anyway.) I don't know if any of this info will help, but here it is:

[http://www.ubuntuforums.org/showthread.php?t=54746](http://www.ubuntuforums.org/showthread.php?t=54746)

---

### Post by filemanager on 2005-08-29
Ok, I found my LiveCD, and I got in, and here are the results from "sudo fdisk -l"

> 
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4865    39078081    c  W95 FAT32 (LBA)
/dev/hda2            4866        9729    39070080    5  Extended
/dev/hda5   *        4866        4871       48163+  83  Linux
/dev/hda6            4872        9612    38082051   83  Linux
/dev/hda7            9613        9729      939771   82  Linux swap / Solaris



(Sorry if it's a bit hard to read :P)

---

### Post by Koba on 2005-08-29
k thanks for that link filemanager but the problem hasn't been resolved in that thread yet :\ thanks for your help anyways, but i'm gunna stil around here to see if anyone else can help, maybe the solution to your problem will fix mine too :P

---

### Post by jlacroix on 2005-08-29
Your fdisk looks fine too. Wierd.

My problem isn't fixed either. I can boot with kernel 2.6.10, but I tried recompiling to get 2.6.12 and it won't work, no matter what I do...

Did gcc do something wierd? I wonder...

---

### Post by godzero on 2005-08-29
I've ran into this problem before. In my case it was certain programs messing with my grub config. If you have a old copy of grub config, you can boot into a live disk and overwrite the new copy with the old, elsewise durring boot you can try to edit your kernal options. I keep copys of certain subdirs (/boot and /etc) around for this reason.

If you do manage to boot back up, reinstall your kenal(s).

---

### Post by Koba on 2005-08-29
k i'm on my live cd right now, is there a way to check my menu.1st file from here? (or w/e its called) and what other info do you guys need while i'm here, i did that fdisk thing and got this:
```
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9733    57697447+  83  Linux
```

---

### Post by Koba on 2005-08-29
AHA! i found my menu.lst file, heres what it had to say:
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
## by the debian update-grub script except for the default optons below

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
if there is anything that could do for you to help me... there it is...

---

### Post by jlacroix on 2005-08-29
Looks good to me. Sorry I wish I could help more.

---

### Post by Kaijec Torsf on 2006-01-10
heheheee......If you forget this step, even if you've done everything correctly up to this point, your system won't be able to boot the new kernel. Your old, existing kernels will still boot, it's just the new kernel which won't boot, so if you forget to do this step, you can still get back into your system and do this later (for some reason, I always forget this step, so that's why I know about this).

Here's why you need to make an intial ram filesystme. In order for your kernel to boot the system, it must be able to read the files on your hard drive in the root (/) filesystem. Your root filesystem is probably formated as ext3, but the default Ubuntu kernel configuration makes the ext3 drivers as kernel modules, which are stored in the root filesystem itself. Since the kernel can't read the root filesystem without the ext3 driver, and the drive is stored in the root filesystem, you're stuck... unless you make the ext3 driver available to the kernel in an inital ram filesystem:

sudo mkinitramfs -o /boot/initrd.img-2.6.12-MYKERNEL 2.6.12-MYKERNEL

The "-o /boot/initrd.img-2.6.12-custom-1" option tells the mkinitramfs command where to send its output, and the "2.6.12-custom-1" at the end of the command line (be sure to preceed this with a space) tells the mkinitramfs command which set of kernel modules to use.

Hope this helps....

Happy Huntung :)

($) T-money ($) ;)

---

### Post by Kaijec Torsf on 2006-01-11
oh yah,

remember to add this line in your (grub) menu.lst
initrd          /boot/initrd.img-2.6.12-MYKERNEL

---

