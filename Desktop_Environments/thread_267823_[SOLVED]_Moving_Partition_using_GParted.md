---
title: "[SOLVED] Moving Partition using GParted"
date: 2006-09-29
forum: Desktop Environments
---

### Post by wieman01 on 2006-09-29
Opening this up for another user... Continue from here:

[http://www.ubuntuforums.org/showthread.php?t=267155&page=2]("http://www.ubuntuforums.org/showthread.php?t=267155&page=2")

---

### Post by wieman01 on 2006-09-29
Ok, let me try to get this right... You're objective is to:

1. delete hda2, hda4, and the 2nd /swap I can see from the image
2. preserve hda1 (Ubuntu /root) and hda5 (Ubuntu /swap)
3. merge the unallocated space with hda1 so as to create on big partition.

Is that correct? Result is that you'll only have 1 x root and 1 x swap. Please confirm so that we can go ahead.

You have the Live CD on hand, don't you?

---

### Post by Psquared on 2006-09-29
Almost. My goal is to merge hda2 and 4 and preserve hda1 so I will have 2 large partitions and move the boot partition to hda1. Right now, as you can see, hda4 is the boot partition. In the end I want to have an 80 gig partition that is empty that i can format for Vista RC1. I know the Vista installer will wipe out the MBR and write its own so I will need to restore Grub once I am finished. I have the Linux rescue disk handy.

---

### Post by ingo on 2006-09-29
Right, having tried my hand at gparted myself I reckon I've found the root to your particular problem. Have a look at this:

[http://www.gnu.org/software/parted/#features](http://www.gnu.org/software/parted/#features)


In particular Note 1 "The start of the partition must stay fixed." is a bit of a killer...

Not knowing your particular partition table there is not really a way of helping you (I don't think). Can you post the blurb from 
$ fdisk -l
that'll give us the cylinders and
$ df
which will give us size, occupied space and free space for each partition. 

Take it from there:D

---

### Post by Psquared on 2006-09-29
> **ingo said:**
> Right, having tried my hand at gparted myself I reckon I've found the root to your particular problem. Have a look at this:

[http://www.gnu.org/software/parted/#features](http://www.gnu.org/software/parted/#features)


In particular Note 1 "The start of the partition must stay fixed." is a bit of a killer...

Not knowing your particular partition table there is not really a way of helping you (I don't think). Can you post the blurb from 
$ fdisk -l
that'll give us the cylinders and
$ df
which will give us size, occupied space and free space for each partition. 

Take it from there:D

I'm at work now so I'll do that tonight. Why can't I use the rescue disk to reinstall Grub on hda1 after I delete and merge hda2 & 4 using gparted? As long as I can boot to hda1 I'll be fine from there.

Thanks for your interest and help.

---

### Post by wieman01 on 2006-09-29
No, GRUB won't be a problem. Don't worry, I have done this a couple of times before. So again, this is what we want, right?

1. hda1 -> root (and boot)
2. merge hda2 & hda4 -> data partition
3. hda5 -> swap

So essentially you'll end up with 3 partitions. If I get it right now, we can continue and do this step by step.

---

### Post by wieman01 on 2006-09-29
Assuming that this is right, we will have to move GRUB to **hda1** first. If anything goes wrong, we can always use the Live CD to recover your partitions. So this is fairly safe. That said I'll get back to you later today and post the steps. :-)

Perhaps read this in the meantime so you know what we are going to do:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Psquared on 2006-09-29
> **wieman01 said:**
> Assuming that this is right, we will have to move GRUB to **hda1** first. If anything goes wrong, we can always use the Live CD to recover your partitions. So this is fairly safe. That said I'll get back to you later today and post the steps. :-)

Perhaps read this in the meantime so you know what we are going to do:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")


Yes, you've got it right. I read the link you gave me. Thanks.

Now, will the linux rescue disk work for this? I also have the Ubuntu Live CD but I think it is 5.04. I may have downloaded the live CD for 6.06 I'll have to check and see when I get home.

Thanks for your help.

---

### Post by wieman01 on 2006-09-29
I think any of those two Live CDs will do. But use the one that matches your version of Ubuntu if possible.

1. Put in the Live CD and boot.
2. Open terminal.
3. Type:
> sudo grub
4. Type:
> root (hd0,0)
5. Type:
> setup (hd0)
6. Type:
> quit
7. Mount hda1:
> sudo mount /dev/hda1 /mnt
8. Make a safety copy of GRUB's config file:
> sudo cp /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst_backup
9. Open GRUB config file:
> sudo gedit /mnt/boot/grub/menu.lst
10. Look for this section:
> title		Ubuntu (blah blah)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.15-25-386 [COLOR="Red"]root=/dev/hda1[/COLOR] ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot
11. Ensure that root is [COLOR="Red"](hd0,0)[/COLOR] and kernel [COLOR="Red"]...root=/dev/hda1...[/COLOR].
12. Save if you have made any changes.
13. Reboot the computer & check if the changes have taken effect.

Note that your menu.lst section might look a bit different, that's alright. But I guess you get the idea now. Let us know how it goes... The next step is to merger your partitions (hda2 & hda4).

---

### Post by Psquared on 2006-09-29
Thanks, giving it a try right now.

---

### Post by wieman01 on 2006-09-30
> **Psquared said:**
> Thanks, giving it a try right now.
Uhuh... Does no response mean something has gone wrong?

---

### Post by Psquared on 2006-09-30
yeah - I can't get the Ubuntu 6.06 Live CD to boot. I even turned off all the boot options except my CD/DVD player in the bios and it says there is an error and it can't boot the live CD. So, either I have to download and burn another one or use something else.

I have a Linux rescue disk and I also have Linux Gparted Live CD. The former is pretty old, but the latter is recent. Will either one work or will have to just try them and see?

---

### Post by wieman01 on 2006-09-30
I cannot tell for sure if these work. They should - but then again I don't if the version of GRUB is right. If you have capacity to download the latest Live CD I would opt for that.

---

### Post by Psquared on 2006-09-30
no luck with the other CDs so i'll download the most recent ubuntu live CD. will take a little while.

thanks for hanging in there with me.

btw, the live cd i have i used to install ubuntu and it is on a CDRW. possibly something got changed during install since it is writeable???

---

### Post by wieman01 on 2006-09-30
> **Psquared said:**
> no luck with the other CDs so i'll download the most recent ubuntu live CD. will take a little while.

thanks for hanging in there with me.

btw, the live cd i have i used to install ubuntu and it is on a CDRW. possibly something got changed during install since it is writeable???
Beats me...

Once you have the Live CD we can continue from there. We'll get this done somehow. :-)

---

### Post by Psquared on 2006-09-30
almost there - 15 more minutes til download complete

---

### Post by Psquared on 2006-09-30
Hmmmm.... I found my rescue disk so I booted from that and followed your instructions. Not everything worked like I expected it to, but it did boot to hda1 and here is the menu.lst file from Grub on that partition;

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


When I run gparted it still shows hda4 with the boot label beside it.

As here:

[img]http://img287.imageshack.us/my.php?image=screenshotrb4.png[/img]

---

### Post by Psquared on 2006-09-30
OK - got the ISO downloaded and made the Live CD. Booted to it and followed your instructions. I am definitely booting from hda1 because I recognize the Grub menu.lst. However, gparted STILL shows hda4 with the label "boot" as the image above shows.

Does that mean anything? If not, lets move on to merging those partitions so i can format and install Vista. 

I'm going to guess and say that I can do this from gparted and then format and install Vista on the newly merged partition, then boot the Live CD and reinstall Grub again.

Is that about right?

---

### Post by wieman01 on 2006-09-30
> **Psquared said:**
> OK - got the ISO downloaded and made the Live CD. Booted to it and followed your instructions. I am definitely booting from hda1 because I recognize the Grub menu.lst. However, gparted STILL shows hda4 with the label "boot" as the image above shows.
No sure why your system does that but I checked my computer and it has no boot flag at all. So I reckon this has no meaning at all... although I could be mistaken here. Since it boots from hda1 we should not worry too much.
> **Psquared said:**
> Does that mean anything? If not, lets move on to merging those partitions so i can format and install Vista.
Merging will be no problem now. But I am a bit worry about VISTA to be honest. I cannot tell if VISTA will let you install the system on any other partition than hda1... I know XP has an issue with that.
> **Psquared said:**
> I'm going to guess and say that I can do this from gparted and then format and install Vista on the newly merged partition, then boot the Live CD and reinstall Grub again.

Is that about right?
Generally that's a yes. But frankly I'd rather free up hda1 for VISTA and move Ubuntu to hda2 or other.

[COLOR="Red"]What's your idea? Merging will be a piece of cake now, however, let's first see if we really want to leave Ubuntu on hda1 in that case.[/COLOR]

As for merging the process looks like this:
> 1. Boot from Live CD
2. Run GParted
3. Delete partition & merge them
4. Edit "/etc/fstab" to reflect the changes in partition numbering
5. Reboot & enjoy
I will write down all the details when you have made up your mind as to where Ubuntu should eventually be installed (partition).

---

### Post by Psquared on 2006-10-01
Too late. Vista is installed. Not sure if it installed itself on the unallocated space created by merging hda2 & 4 or not. Hadn't thought of moving Ubuntu to that new space.

So how do I find out if Ubuntu is still there?

Boot the Ubuntu Live CD again?

---

### Post by wieman01 on 2006-10-01
Oh man... Ok, the only way to find out is boot from Live CD. Good luck! Let me know if I can be of any help.

---

