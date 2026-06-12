---
title: "add ubuntu 9.04 to grub menu?"
date: 2009-05-15
forum: General Help
---

### Post by wendallsan on 2009-05-15
Hi all,

I have a hard drive with several OS's on it.  I have just repartitioned it to make room for more.  I put ubuntu 9.04 on one partition, but grub is still loading from one of my other partitions.  I'd like to be able to add 9.04 to the menu it's currently using and continue using grub as-is (instead of switch to the grub that was set up with the Ubuntu 9.04 install), and have found my /boot/grub/menu.lst on the relevent partition file and added what I found in my 9.04 partition's menu.lst file:
```

title Ubuntu 9.04, kernel 2.6.24-21-generic
root (hd0,2) # I ADDED THIS LINE MYSELF . . .
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

```
I added the root line, which I believe is the right partition that I'm trying to boot from (I've also tried all the other partition numbers in desperation).

When I reboot and selet this item from the grub menu I get the following error:

Error 2: Bad file or directory type

Using gparted, I can see the partitions on my hard disk: /dev/hda3 is the partition I want to boot to.  If I've read my grub docs right that corresponds with the 'root (hda0,2)' bit of the menu item, so I think I have this much correct.

Any ideas?  Any help is greatly appreciated!

---

### Post by Brandon Williams on 2009-05-15
The first thing that I notice is that you're telling it to use the 2.6.24-21 kernel, but an initrd image for the 2.6.28-11 kernel. You probably want to fix that first and see if that solves the problem.

The next possibility is that you need a different stage1 bootloader to read the root filesystem of your 9.04 install. Did you format that partition at ext4? I don't know whether the older version of grub can handle ext4. It seems like it should, but I'm not certain. I'm not certain what the right approach is if this turns out to be the problem, but I would probably switch to using the Jaunty partition as my root for the bootloader.

FWIW, if I were setting this up, I would set up grub to chainload the Jaunty bootloader, rather than explicitly specifying the kernel information in the other version's menu.lst. If you chainload Jaunty, then it will read the Jaunty menu, allowing you to easily boot Jaunty into recovery mode, and it will also automatically use new Jaunty kernels when they get installed.

---

### Post by Kevbert on 2009-05-15
The other thing you may want to check is the uuid of the drive where 9.04 is installed is correct with
```
ls /dev/disk/by-uuid -lah
```
The current kernel for 9.04 is 2.6.28-11.

---

### Post by lightstream on 2009-05-15
.. and also, instead of using root(blah), you can specify the partition by UUID:

```
title Ubuntu 9.04, kernel 2.6.24-21-generic
UUID 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by reevine on 2009-05-16
yes by using the UUID instead of root you can specifically identify your 9.04 partition. root is basically for other operating systems.

> The first thing that I notice is that you're telling it to use the 2.6.24-21 kernel, but an initrd image for the 2.6.28-11 kernel. You probably want to fix that first and see if that solves the problem.


re: and i do believe you are right there. 

boot into another ubuntu system and check your files in your /boot/grub/ folder. make sure that your kernel is correct as suggested from above.

---

### Post by reevine on 2009-05-16
yes by using the UUID you specifically identify the 9.04 system no matter what partition. root is ment for other operating systems.
and i do beleive also that your kernel is wrong too as mention above. you should have this as your kernel:

/boot/vmlinuz-2.6.28-11-generic

if you want you can even make a dedicated GRUB partition that isnt attached to any system. if you do that then you can delete as many operating systems as you would like and not affect GRUB at all.

Edit: srry for the double post. internet was freakn' out. lol

---

### Post by wendallsan on 2009-05-16
Hi all,

thanks for all the feedback.  I think once I'm done with this, I'll actually really understand GRUB instead of just be using it . . .

I've updated my GRUB entry:

```

title Ubuntu 9.04, kernel 2.6.24-21-generic
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic 
initrd /boot/initrd.img-2.6.28-11-generic
quiet

```

I've switched from root to uuid to identify the partition, and have double checked with the 9.04 grub menu.lst file that I've got the right partition.

I can mount the partition and verify that there's a kernel at /boot/vmlinuz-2.6.28-11-generic and an initrd at /boot/initrd.img-2.6.28-11-generic.

When I select this menu item in grub, I still get an error 15: file not found.

Any further help is appreciated.  I'll also look into chainloading over to the Ubuntu 9.04 grub today . . .

thanks again!

---

### Post by reevine on 2009-05-16
> **wendallsan said:**
> Hi all,

thanks for all the feedback.  I think once I'm done with this, I'll actually really understand GRUB instead of just be using it . . .

I've updated my GRUB entry:

```

title Ubuntu 9.04, kernel 2.6.24-21-generic
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic 
initrd /boot/initrd.img-2.6.28-11-generic
quiet

```

I've switched from root to uuid to identify the partition, and have double checked with the 9.04 grub menu.lst file that I've got the right partition.

I can mount the partition and verify that there's a kernel at /boot/vmlinuz-2.6.28-11-generic and an initrd at /boot/initrd.img-2.6.28-11-generic.

When I select this menu item in grub, I still get an error 15: file not found.

Any further help is appreciated.  I'll also look into chainloading over to the Ubuntu 9.04 grub today . . .

thanks again!
do you have multiple ubuntu installations? if so go into terminal and type:

```

sudo grub
find /boot/grub/stage1

```

and let me know what you get.

---

### Post by wendallsan on 2009-05-16
I do have multiple Ubuntu installs, an 8.04 and a 9.04.
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd0,5)

```

---

### Post by reevine on 2009-05-16
> **wendallsan said:**
> I do have multiple Ubuntu installs, an 8.04 and a 9.04.
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd0,5)

```
do you have windows installed?

---

### Post by wendallsan on 2009-05-16
I don't have Windows installed, but would like to install XP on hda4 eventually.

---

### Post by reevine on 2009-05-16
ok so you only have two ubuntu installations. allright go into the terminal and type:

```

sudo grub
geometry (hd0)

```

let me know what you get then.

Edit: This command will give us the exact information on your hard drive and partitions.

---

### Post by wendallsan on 2009-05-16
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/hda   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83

Thanks again!

---

### Post by reevine on 2009-05-16
> **wendallsan said:**
> grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/hda   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83

Thanks again!
ok now what we want to do is fix grub. type this in the terminal:

```

sudo grub
root (hd0,5)

```

this tells grub where to get the directional files that it needs. then enter this:

```

setup (hd0)
quit
sudo shutdown -h -P now

```

this will tell grub to install itself again with the root files that we told it to use. then  other command is to do a complete shutdown. just start up the computer again and select 9.04 again and see if that works.

---

### Post by wendallsan on 2009-05-17
Hi and thanks again for the help.

I executed the commands above, and they completed successfully.  On rebooting, I'm presented with the same grub menu that I've been working with from the start, and none of the options on the menu are behaving any differently.  My 2 'old' OS's (Ubuntu 8.04 and 64Studio) are still booting fine.  Trying to boot to Ubuntu 9.04 gives me the same error:

```

Error 15: File not found

```

Here's my entire menu.lst file in case there's something there that is messing things up that I'm not aware of.

```


default		0
timeout 	10
color cyan/blue white/blue

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
# kopt=root=/dev/hda6 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

### END DEBIAN AUTOMAGIC KERNELS LIST

title		64studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot

# NOW AN ATTEMPT TO GET UBUNTU 9:

title Ubuntu 9.04, kernel 2.6.24-21-generic
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Chainload to Ubuntu 9.04
# root (hd0,2)
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
chainloader +1

# COPIED FROM THE UBU 9.04 PARTITION BOOTLOADER FOR REFERENCE
# title		Ubuntu 9.04, kernel 2.6.28-11-generic
# root		(hd0,2)
# uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash 
# initrd		/boot/initrd.img-2.6.28-11-generic
# quiet

```

---

### Post by Brandon Williams on 2009-05-17
Ignoring the chainloader stuff for the moment, since you've got a separate active thread for that, I notice that you haven't specified a kernel root parameter for the 9.04 boot. I think that this: 'kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash', should be this: 'kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash'.

In fact, if it were me, I would just use the one that you copied from the 9.04 install.

Also, as noted in the chainloader thread, the version of grub that came with your Ubuntu 8.04.1 install might not be able to handle the filesystem set up by the 9.04 installer. Consider installing the grub stage1 from the 9.04 live CD to your MBR, though this won't be necessary if you get the chainloader option working.

---

### Post by reevine on 2009-05-17
> **Brandon Williams said:**
> Ignoring the chainloader stuff for the moment, since you've got a separate active thread for that, I notice that you haven't specified a kernel root parameter for the 9.04 boot. I think that this: 'kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash', should be this: 'kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash'.

In fact, if it were me, I would just use the one that you copied from the 9.04 install.

Also, as noted in the chainloader thread, the version of grub that came with your Ubuntu 8.04.1 install might not be able to handle the filesystem set up by the 9.04 installer. Consider installing the grub stage1 from the 9.04 live CD to your MBR, though this won't be necessary if you get the chainloader option working.
Ya Williams is right about your kernel root.
if you look at your copied reference you will see that you forgot to add it in. After you fix that just reload GRUB again from the terminal like you did before.

---

