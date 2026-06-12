---
title: "partitions, moving them around, changing place, etc."
date: 2006-09-28
forum: Desktop Environments
---

### Post by crash0 on 2006-09-28
i have two partitions:
1. hda1, 4 gb
2. hda3, 20 gb

(+ hda5 > swap partition, 1 gb i think)

the problem is that my root is on hda1 and it doesen't have much place left. hda3 has some 10 gb free space left. i used the live cd to boot dapper and tried gparted to resize the partitions. all i can do is make the hda1 or hda3 smaller. this is how it's graphicaly displayed:

[------HDA3 used------HDA3 free ] [---HDA1 used-HDA1 free] [swap]

when i choose resize, i can move the hda3 to the LEFT (make it smaller) and then free space appears. however, i can't move hda1 to the left (to make it bigger), i just get a block of free space i can't merge with hda1.

so what i need is a solution how to transfer 2-3 gb of free space from hda3 to hda1.

thank you in advance...

---

### Post by wieman01 on 2006-09-28
You're close. Free up space on **hda3** (bigger than 4 GB to begin with), then create a new partition and copy **hda1** to the new partition, delete the "old" root partition (hda1), and resize "new" root.

Then you have to edit:
1. /etc/fstab
2. GRUB
3. /boot/grub/menu.lst

The resizing is not an issue I think. Do you know how deal with "fstab" and  "grub"?

---

### Post by Psquared on 2006-09-28
> **wieman01 said:**
> You're close. Free up space on **hda3** (bigger than 4 GB to begin with), then create a new partition and copy **hda1** to the new partition, delete the "old" root partition (hda1), and resize "new" root.

Then you have to edit:
1. /etc/fstab
2. GRUB
3. /boot/grub/menu.lst

The resizing is not an issue I think. Do you know how deal with "fstab" and  "grub"?

Sorry to butt in, but I have a similar problem/issue.

I have a 160 gig HD divided into 3 main partitions. Hda1, 2 & 4. (plus the swap which is 5 i think)

I installed, in order Ubuntu 6.06 Hda1; Kubuntu 6.06 Hda4 and Xubuntu on Hda2. I know they are out of order and I just made a mistake during install and picked the wrong partition. Anyway, Hda2 is the boot parition according gparted. I would like to move the boot to Hda1 and delete the other two partitions. I've already copied over everything I need from the other partitions to Hda1.

If I start gparted with gksudo will it let me move these around just by grabbing them and moving them. Or is there a way to just change the boot designation to Hda1. I realize I will have to either reinstall grub or edit the existing grub on Hda1 - I can handle that, but messing with partitions makes me apprehensive. I don't want my system to become unbootable.

Thanks.

---

### Post by ingo on 2006-09-28
Right, first of all be VERY careful...

Then copy your /usr directory, after all this is where most of your stuff is stored, into the empty partition. Use your favourite editor to add the following line to your fstab:

/dev/your_empty_partition   /usr   ext3 (or whathaveyou) acl,user_xattr     1 1

Reboot. If everything goes (and it should unless there's a typo somehwere) well you can delete 
the /usr directory from your full partition.

---

### Post by wieman01 on 2006-09-28
> **ingo said:**
> Right, first of all be VERY careful...

Then copy your /usr directory, after all this is where most of your stuff is stored, into the empty partition. Use your favourite editor to add the following line to your fstab:

/dev/your_empty_partition   /usr   ext3 (or whathaveyou) acl,user_xattr     1 1

Reboot. If everything goes (and it should unless there's a typo somehwere) well you can delete 
the /usr directory from your full partition.
Hang on a minute. I occurs we're not on the same page... Why "/usr"? That's not what these guys are asking for. Or am I wrong?

---

### Post by wieman01 on 2006-09-28
> **Psquared said:**
> Sorry to butt in, but I have a similar problem/issue.

I have a 160 gig HD divided into 3 main partitions. Hda1, 2 & 4. (plus the swap which is 5 i think)

I installed, in order Ubuntu 6.06 Hda1; Kubuntu 6.06 Hda4 and Xubuntu on Hda2. I know they are out of order and I just made a mistake during install and picked the wrong partition. Anyway, Hda2 is the boot parition according gparted. I would like to move the boot to Hda1 and delete the other two partitions. I've already copied over everything I need from the other partitions to Hda1.

If I start gparted with gksudo will it let me move these around just by grabbing them and moving them. Or is there a way to just change the boot designation to Hda1. I realize I will have to either reinstall grub or edit the existing grub on Hda1 - I can handle that, but messing with partitions makes me apprehensive. I don't want my system to become unbootable.

Thanks.
A screenshot of GParted would help, perhaps it's also advisable to post your "/etc/fstab" file to start with. If you need a hand with GRUB, let us know. 

Don't worry about messing around with the partitions. You can always recover your system with the Live CD. Done it a couple of times. But do a backup of your personal files before we continue.

---

### Post by ingo on 2006-09-28
> **wieman01 said:**
> Hang on a minute. I occurs we're not on the same page... Why "/usr"? That's not what these guys are asking for. Or am I wrong?

Well, you're quite right. All the above does is free up space on a partition. It does so reliably and cleanly (which gparted, I am afraid to say, has failed to do whenever I used it). 

OK, so your partitions are still out of sync, but you can carry on working the system. Proper solution would of course be using partimage, wipe your hd clean and start again, that little bit wiser:)

---

### Post by daxelrod on 2006-09-28
> **crash0 said:**
> 

[------HDA3 used------HDA3 free ] [---HDA1 used-HDA1 free] [swap]

when i choose resize, i can move the hda3 to the LEFT (make it smaller) and then free space appears. however, i can't move hda1 to the left (to make it bigger), i just get a block of free space i can't merge with hda1.

I suggest the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"). It has a much newer version of GParted that has much better support for moving partitions. (Which is what you want to do. Extending HDA1 to the left will require actually moving the partition.) Basically, the dialog box for resizing partitions will let you exend HDA1 how you expect.

Note that if you boot from the GParted LiveCD and get a blank screen when it tries to launch the graphical interface at the end of booting, try selecting the Vesa Xserver in the boot options menu.

---

### Post by ingo on 2006-09-28
hm, thanks daxelrod. seems to be a great tool, trying it out at the mo...

---

### Post by crash0 on 2006-09-28
> **wieman01 said:**
> You're close. Free up space on **hda3** (bigger than 4 GB to begin with), then create a new partition and copy **hda1** to the new partition, delete the "old" root partition (hda1), and resize "new" root.

Then you have to edit:
1. /etc/fstab
2. GRUB
3. /boot/grub/menu.lst

The resizing is not an issue I think. Do you know how deal with "fstab" and  "grub"?

yes i thought about copying it but here is the reason why it doesent make sense:
i want to give hda1 (the boot partition) 2 more gb. if i reduce hda3 for 4 gb and copy it, etc., etc., i'll get two partitions that are approx. the same size. i don't wan't what, i wan't to redce hda3 by maximumly 2 gb and give those 2 gb to hda1.

also, about grub and fstab... i worked with that some time ago when i designated some old partitions, but i don't know what to do in this case.

---

### Post by ingo on 2006-09-28
Right, having used partimage (thank God!) I tried the gparted live cd. Moved a few partitions, deleted some, created others. So far so good, did everything without returning error messages. Did a reboot and lo and behold my superblocks are all over the place :( System still booted but I have to control D every time to ignore the file system check.Next step was: 

$ mke2fs -n /dev/hda2

and got told about all the superblocks at my disposal. Tried them all with 

$ e2fsck -b xxxxxxx /dev/hda2

and always got following response:


e2fsck: Invalid argument while trying to open /dev/hda2
The superblock could not be read or does not describe a correct ext2 filesystem... 

Hm, this is not what I was hoping for. Anybody point me in the right direction?

---

### Post by Psquared on 2006-09-28
> **wieman01 said:**
> A screenshot of GParted would help, perhaps it's also advisable to post your "/etc/fstab" file to start with. If you need a hand with GRUB, let us know. 

Don't worry about messing around with the partitions. You can always recover your system with the Live CD. Done it a couple of times. But do a backup of your personal files before we continue.

Will do when I get home tonight. Thanks. I played around with Kubuntu and Xubuntu but I keep going back to Gnome so there's no point in keeping the others. Besides, Kubuntu was borked by a kernel upgrade and won't start anyway and Xubuntu was borked by me because I tried to compile some non-debian stuff.  ](*,)

---

### Post by Psquared on 2006-09-28
> **wieman01 said:**
> A screenshot of GParted would help, perhaps it's also advisable to post your "/etc/fstab" file to start with. If you need a hand with GRUB, let us know. 

Don't worry about messing around with the partitions. You can always recover your system with the Live CD. Done it a couple of times. But do a backup of your personal files before we continue.

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

This is not going to help you much because I have an fstab file in Xubuntu too. I'll see if I can post that one. (I have one in Kubuntu too)

I took a screen shot of gparted which I will also post.

---

### Post by Psquared on 2006-09-28
Hey, how do I post a screenshot? Do I put it in the gallery?

---

### Post by Psquared on 2006-09-28
> **Psquared said:**
> Hey, how do I post a screenshot? Do I put it in the gallery?

Here we go:

[img]http://img204.imageshack.us/img204/366/screenshotot8.png[/img]

---

### Post by wieman01 on 2006-09-29
Hello Psquared:

I have opened up a new thread for you: [http://www.ubuntuforums.org/showthread.php?p=1558646#post1558646]("http://www.ubuntuforums.org/showthread.php?p=1558646#post1558646")

Don't want to hijack this one. See you soon.

---

