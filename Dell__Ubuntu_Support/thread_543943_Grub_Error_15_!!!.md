---
title: "Grub Error 15 !!!"
date: 2007-09-05
forum: Dell  Ubuntu Support
---

### Post by El Lance-O on 2007-09-05
So I know there are threads about this all over the internet, but none of them are caused by the same reason, or the intructions are quite vague, at least to this Linux n00b.

Oh and the reason I posted this in the Dell forums is because I am using a Dell Inspiron 1505n.

Here's what I get.

When I boot, I get:

```
Error 15: File not found

Press any key to continue...
```

So I do, which puts me in the GRUB menu:

```
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16 (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15 (recovery mode)
Ubuntu, memtest86+
Reinstall Operating System (WARNING: all Hard Drive data will be lost)
```

None of which works, and I am definitely not going to reinstall everything, that is NOT an option here.

I also do not have a LiveCD at this moment,  but I can get one to fix the problem if it requires it.

As I said before, I am quite the Linux n00b, so I am going to have to be walked through this. I know basic commands, but nothing to fix a kernel error whatsoever.

Please help soon, this computer is my life, and it's at a standstill until this is fixed.

Thanks ahead of time!

---

### Post by rsambuca on 2007-09-05
What did you do prior to this error occuring?

And please use more appropriate thread titles in the future.

---

### Post by El Lance-O on 2007-09-05
Haha, sorry. Humor is the only thing getting me by at this point.

All that happened prior was a normal update which required me to restart. The only update I remember was linux-headings or something to that extent.

From reading the other posts about the matter, I think the kernel was updated and it modified an entry incorrectly.

Thanks for replying.

---

### Post by rsambuca on 2007-09-05
Looks like after the kernel update your grub got messed up a bit.  If none of those boot options will work for you, then you will need to get a hold of a liveCD so that we can fix your grub.

---

### Post by El Lance-O on 2007-09-05
Well I have that set up, I'll have it in a couple hours, in the meantime, type up some instructions for me so I can have it all together by then.

---

### Post by nermalthecat on 2007-09-05
Okay, here is everything you need to know.

1) Boot into the livecd

2)Open up Terminal

3)type: "sudo su"    (to become root)

4)type: "grub"

5)type: "find /boot/grub/stage1"

6)Then it will display where grub is installed. If you have it installed to the mbr, it'll say (hd0), but it may be different depending on where it is installed (on my machine it's (hd0,3)) on your machine.

##make sure you type exactly what was displayed

7)type: "root (whatever the previous command displayed)

8 ) now type: "setup (the same thing you entered in the step 7 brackets)"

9)now type: "quit"

10) reboot, and remove the cd. Hopefully it works properly afterwards!

---

### Post by El Lance-O on 2007-09-06
Well...unfortunately as soon as I use the 'find /boot/grub/stage1' I get another Error 15.

This isn't looking good... :(

---

### Post by pentolino on 2007-09-06
I have the same problem; it seems my hard disk is dying...
I also have another partition (ext2) for which I can't do e2fsck for ANY of the superblocks, they all seem wrong.
Windows on another partition is working fine till now, so I made a backup and I can try to recover but I think the best thing will be to reformat and pray... it has to live just until Mac Os 10.5 is out, then I'll buy a new one!
Note that everything is ok in Grub conf, it can read menu list but it strangely can't read the corresponding image files, none of those...
Do I have any hope to recover something?
Thanks for any info provided :-)
Riccardo

---

### Post by kallistra on 2007-09-06
If you're getting that error after a header update, I got the same thing. What happened is my grub was thinking my boot hard drive was elsewhere. When you are in the grub menu at a normal startup, hit e to edit the line for the boot option, say the top one.

Then edit the line that is root (hd0,1) for instance, yours may be different.

Here is my after update grub items:

```

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,5)

```Now, root (hd0,5) points to my home partition. So I edited like so...

```

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,4)

```hd0,4 is my root partition.

By trying it out during the grub menu, it'll let you do edits for hd0,0 hd0,1 hd0,2 .... you get my point? After you make the change (do only one at a time), press 'b' to boot it. If it works, you know what you want to use to edit your menu.lst with. And you don't need a liveCD to do this either.

Once you boot properly, you'll want to edit your menu.lst.

```

sudo gedit /boot/grub/menu.lst

```And fix the bad root locations.

Let me know if that works for you.
Anyways, please let me know if this helps or if anything isn't clear.

---

### Post by El Lance-O on 2007-09-06
Alright, so I actually sat down and looked around, and here's what I found:

I have 4 partitions, 'DellUtility', 'OS', 'os_part', and 'os_part (2)'.

Under os_part (2), there was a folder, 'grub', which caught my eye, and it did indeed have a 'stage1' file in it.

Also, there was several files that looked familiar:

abi-2.6.20-15-generic
abi-2.6.20-16-generic
config-2.6.20-15-generic
config-2.6.20-16-generic
initrd.img-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak
initrd.img-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak
memtest86+
System.map-2.6.20-15-generic
System.map-2.6.20-16-generic
vmlinuz-2.6.20-15-generic
vmlinuz-2.6.20-16-generic

So I went back to the terminal, used your instructions again and this is what I got:

```
grub> find /grub/stage1
 (hd0,2)

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,2) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.
```

I also looked in /boot, and only found:

```
root@ubuntu:/home/ubuntu# cd /boot
root@ubuntu:/boot# dir
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic
```


So what to do now? It didn't work, I still get the same error when I boot.

What to do now?

---

### Post by rsambuca on 2007-09-06
You ran the "setup" option incorrectly.  What that command does is send the small stage 1 grub instructions somewhere, which in your case should just be (hd0).

---

### Post by El Lance-O on 2007-09-06
Alright, this is what I got this time, and I will tell you what happens after I reboot..

```
grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,2)/grub/stage2 /grub/menu
.lst"... succeeded
Done.
```

---

### Post by El Lance-O on 2007-09-06
Nope :(

I did what kallistra suggested, even changing the two lines after root to /grub instead of /boot because I noticed there wasn't a 'grub' folder in /boot.

Still didn't work.

Should I move the 'grub' folder to /boot?

I was curious why there was two 'os_part' partitions...

---

### Post by El Lance-O on 2007-09-07
WOO!!!

I got it to work!

So I moved the contents of 'os_part (2)' into the /boot folder of 'os_part', and rebooted.

It didn't work at first, I had to edit the 'root (hd0,2)' line to 'root (hd0,5)'.

Now I am curious as to what actually happened here, for some reason the update moved everything under /boot to another partition of the same name, so what is to happen with that partition?

How would I go about removing it?

---

### Post by rsambuca on 2007-09-07
The update couldn't have done that.

Could you please post the output of ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
```

---

### Post by El Lance-O on 2007-09-07
Sure thing.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         269     2104515    b  W95 FAT32
/dev/sda3   *         270         294      200812+  83  Linux
/dev/sda4             295        9729    75786637+   f  W95 Ext'd (LBA)
/dev/sda5             295         456     1301233+  82  Linux swap / Solaris
/dev/sda6             457        9729    74485341   83  Linux
```

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e5fa576c-ab97-4b08-a124-105c154482fd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e5fa576c-ab97-4b08-a124-105c154482fd ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e5fa576c-ab97-4b08-a124-105c154482fd ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e5fa576c-ab97-4b08-a124-105c154482fd ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e5fa576c-ab97-4b08-a124-105c154482fd ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz
```

---

### Post by rsambuca on 2007-09-07
I see now that you had a separate boot partition.  Did you set this up yourself, or did someone else do it for you?

---

### Post by El Lance-O on 2007-09-16
Sorry to take so long to reply, I gave up on technology for a while and got the last bit of camping in before the winter.

I haven't done any partitioning at all since I've had it. It's how it came I guess, like kallistra said, an error after a header update.

Before I left I just edited the command everytime during the boot. I just now edited menu.lst.

I'll assume it'll work, but if not I will be sure to reply quickly.

Thanks for everyones help, I really do appreciate it. I would be completely lost without you guys. :popcorn:

---

