---
title: "Help with Grub - multiple installs on same HD"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Psquared on 2006-09-09
See my post:

[http://www.ubuntuforums.org/showthread.php?t=167016](http://www.ubuntuforums.org/showthread.php?t=167016)

I am wondering if it would be easier to just reinstall Grub and let it detect everything. However, I would like the entries to say: 

Ubuntu - Gnome
Kubuntu
Xubuntu

with only the latest kernels showing.

Any help would be greatly appreciated.

---

### Post by infoseeker on 2006-09-09
Grub =/= kdm or gdm :D

---

### Post by Psquared on 2006-09-09
> **infoseeker said:**
> Grub =/= kdm or gdm :D

Is that a command to run in terminal or are you asking me a question??

---

### Post by Herman on 2006-09-09
Hello, Psquared,
Can you please post the outpit from 'sudo fdisk -lu' here?```
sudo fdisk -lu
``` Regards, Herman :D

---

### Post by kflorek on 2006-09-09
> **Psquared said:**
> See my post:

[http://www.ubuntuforums.org/showthread.php?t=167016](http://www.ubuntuforums.org/showthread.php?t=167016)

I am wondering if it would be easier to just reinstall Grub and let it detect everything. However, I would like the entries to say: 

Ubuntu - Gnome
Kubuntu
Xubuntu

with only the latest kernels showing.

Any help would be greatly appreciated.

 I am fairly certain Grub does NOT DETECT any OSes. What has been detecting OSes for you is the Ubuntu installer. If you reinstall Grub, it should keep the menu you have, I would think.

 I've got something like what you have: a bunch of OSes. You are right that each X/K/Ubuntu install just does its own GRUB setup; and it picks up all, or most, of what was in the previous boot menu, and besides that adds all, or most all, of the OSs it finds on any existing partitions, and adds recovery mode entries too. It is quite a mess if you have many OSes!

 The partition the "real" Grub menu is in is the one the last ubuntu was installed in. It is located in /boot/grub and called menu.lst. That's just because the LAST install put a loader program in the MBR (Master Boot Record) which was customized to load up stuff from that last partition you installed to.

 Grub menus are simpler than they may seem. The explanation of the entries is often needlessly intricate.

 The line that starts with "title" doesn't do anything. You can put anything in it. I think that is what you really want to know. It is what is put on the boot screen for your information so you can identify an OS. Grub doesn't use it for anything else.

title Ubuntu, kernel 2.6.15-26-386 (on /dev/hda1) (on /dev/hda4)

 You could put
title A
and that would work.

The line that starts with "root" informs grub of the starting point for anything in the following commands - what hard drive, what partition. For reasons known only to the program designer, all the numbers are 1 less than the counting number. The first hard drive (hda) is hd0. The fourth partition (hda4) is 3. Programmers often like to start with 0 instead of 1 :)

root (hd0,3)

The boot process for linux needs two files. The line with "kernel" in it gives the file specification for the first file required. It IS, I presume, the linux kernel, the chunk on which the whole thing depends.

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash

The stuff following the file specification, "root=/dev/hda1 ro quiet", are parameters passed to the linux kernel. The kernel needs some of them. "quiet" is not really needed. It just surpresses a lot of detail that can be put on the screen when the kernel takes over. "splash" briefly puts up a graphic file to spruce up the looks, or inform. You don't need it to boot.



"initrd" gives the file specification of the second file linux needs to boot itself. I don't really know how linux boots itself, but it always needs two files to start off.

initrd /boot/initrd.img-2.6.15-26-386

 Whatever "savedefault" does, most linux distros I have don't have in the grub menu, and Grub works fine without it.

savedefault

Now that Grub knows what it need to know to boot linux, "boot" makes it go at it.

boot

The file specifications have to be exactly right of course. You can't change or leave off anything from "initrd.img-2.6.15-26-386". This is important if you update kernels for an OS besides the LAST one installed, the one that wrote the "menu.lst" menu we are talking about. Let's say you update the SUSE kernel, but the LAST OS that redid the MBR was Ubuntu. SUSE is not going to change the menu.lst on the UBUNTU partition, although it likely will update the menu.lst on its own partition, the SUSE partition. That means you won't be able to boot the new SUSE kernel until you fix the menu on the Ubuntu partition with the exact SUSE names.

 But some distros do this: They make symbolic links to the real file and name the links something like "vmlinuz" for "vmlinuz-2.6.15-26-386" (and initrd.img for "initrd.img-2.6.15-26-386")
Then the Grub menu can have

kernel /boot/vmlinuz root=/dev/hda1 ro quiet

and Grub seems to work just fine with this. You just update the links for new kernels and you don't have to update the grub menu. However, as a precaution, it is a good idea to keep the old kernel around for a while, and have a menu entry for it too.

 Strangely, Ubuntu seems to put appropriate symbolic links in the / directory (not in /boot), and it updates the links when the kernel is updated, but it does not use them in the menu.lst.

 IAC, you could have

kernel /vmlinuz root=/dev/hda1 ro quiet

in the menu.lst and it should work. I have not got around to trying it.

---

### Post by Herman on 2006-09-10
>   Whatever "savedefault" does, most linux distros I have don't have in the grub menu, and Grub works fine without it.kflorek,  You'll see a text file named 'default' in /boot/grub. Grub can write to it and remember the last operating system you booted. 
To make that work, you just type 'saved' after the line that sets the default operating system in menu.lst instead of a number like most people do. (You know, the one that boots when you start your computer early in the morning and go make a cup of coffee and you're not watching it). Anyway, it just means grub will remember your last-booted operating system and boot that again unless you select a different one. I like it that way.
I learned some things from your good explanation about menu.lst, so I though I'd share something back that I know, thanks for your great info. People like you make these forums interesting and fun.
Regards, Herman :D

---

### Post by Psquared on 2006-09-10
> **Herman said:**
> Hello, Psquared,
Can you please post the outpit from 'sudo fdisk -lu' here?```
sudo fdisk -lu
``` Regards, Herman :D


peyre@peyre-desktop:~$ sudo fdisk -lu
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   153597464    76798701   83  Linux
/dev/hda2       153597465   231576974    38989755   83  Linux
/dev/hda3       306536265   312576704     3020220    5  Extended
/dev/hda4   *   231576975   306536264    37479645   83  Linux
/dev/hda5       309556548   312576704     1510078+  82  Linux swap / Solaris
/dev/hda6       306536391   309556484     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order
peyre@peyre-desktop:~$

There ya go. Does that help?

---

### Post by Psquared on 2006-09-10
Thanks guys.

What i did was go into Xubuntu (the last installed) and print out menu.lst. The I rebooted to see what I needed to change. Xubuntu was the last one installed yet it was entitled Ubuntu. I went in and edited the menu.lst and commented out the extraneous stuff, changed Ubuntu to Xubuntu, found the correct Kubuntu entry and commented out old kernels etc. Now when I boot, I see them in the reverse order they were installed. Xubuntu is first (latest kernel and Recovery mode), followed by Kubuntu and then Ubuntu.

It all makes sense now - except for the output of fdisk -lu which seems to say something is out of order?? I think what it is saying is that Xubuntu is on Hda2 and Kubuntu is on Hda4. It should have been the other way around, but I created the two new partitions at the same time so when I installed Kubuntu I put it on Hda4 instead of Hda2. Other than that I am happy with the result.

Thanks for all your help.

---

### Post by Herman on 2006-09-11
Psquared, 
I'm glad you are happy, that's the most important thing at all times. :)

I was wondering if that was really your Xubuntu menu.lst from /dev/hda4 that you posted in that other thread?

... or was it your /dev/hda2 Kubuntu's menu.lst. It looks like it could be that one, because it has,```
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
```, so it should be your Kubuntu installation's menu.lst, from /dev/hda2, right?

...and yet thinks it's Ubuntu?
```
 ## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

```  Well, I'm  still more than a little puzzled and confused. :confused:

I really think you should check the menu.lst of each operating system and make sure that 'kopt' and 'groot' line for your automagic kernels list has the correct partition number after it. 

If your Ubuntu is really on /dev/hda1, then you should have   # kopt=root=/dev/hda1 ro, and  # groot=(hd0,0), in your Ubuntu's menu.lst, on (hd0,0).

If Kubuntu is really on /dev/hda2, then it's menu.lst should have # kopt=root=/dev/hda2 ro, and  # groot=(hd0,1), in your Kubuntu's menu.lst, on (hd0,1).

If Xubuntu is really on /dev/hda4, then it's menu.lst should have # kopt=root=/dev/hda4 ro, and  # groot=(hd0,3), in your Xubuntu's menu.lst, on (hd0,3).

If you have to edit these entries to make them point to the correct partitions, then it is likely that your /etc/fstab files will need editing too. It's nothing very serious at all, but I have a hunch I know what might be wrong. ... or maybe I'm jumping to the wrong conclusion.
Let me know what you find and I'll help you if you need it. ...Or maybe I'm barking up the wrong tree and nothng more needs to be done.

Just check anyway, oh, and thanks for the sudo fdisk output, those are very often indepensible in sorting out all kinds of problems. I always like to see those, they really are a big help.
Regards, Herman :D

---

### Post by kflorek on 2006-09-11
> **Psquared said:**
> 

...

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   153597464    76798701   83  Linux
/dev/hda2       153597465   231576974    38989755   83  Linux
/dev/hda3       306536265   312576704     3020220    5  Extended
/dev/hda4   *   231576975   306536264    37479645   83  Linux
/dev/hda5       309556548   312576704     1510078+  82  Linux swap / Solaris
/dev/hda6       306536391   309556484     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

.....
It all makes sense now - except for the output of fdisk -lu which seems to say something is out of order?? 



 Very few people have a need to know any of the following, so delving into it may be more of a PITA then helpful. It is surperfluous for understanding GRUB. But anyway, demystifying these gratuitous FYI (For Your Information) messages that you see everywhere has a certain value in itself. Then you might know when a message that really counts shows up :)

 What does "Partition table entries are not in disk order" mean? Well, starting from the outer tracks of a hard drive and working inward, you would think that the first partition is the first one, the second partition is the second, the third partition is third, and etc. That would make sense. But it doesn't have to be; partitioning programs frequently don't do it that way, particularly if you resize a partition to make room for one more. The partitioners they have within the installer for the linux distros I have used are so peverse about this that I am tempted to go back to (the excellent) BootItNG.

 The ancient, original DOS/Windows partitioning system (which linux comports with) has a table with four entries.(located in the MBR. yes the master boot program is there also.) The entries have some numbers saying where on the HD a partition is located. But the second entry in the partition table could very well point to the fourth partition (in disk order), and the third entry in the table could point to the second partition (in disk order). In short, the table entries could be in any order going by the order on the HD. Linux and Windows go by the order in the table, not disk order.

 If you look at the table entry with the star next to it, notice that the beginning number is less than the beginning number of the entry before it: it is out of disk order. Although Linux and Windows don't care, unfortunately (for me) I have run into utilities that go bonkers when they see this!

 Any entry could also be a null or empty entry. There don't have to be four existent partitions. But Linux reserves hdx1 to hdx4 for these even if some are nulls.

 Because most people use Windows, most often there is just one entry in this table. Second most often there are two.

 That is enough of an explanation, except that people know there can be more than four partitions. So for clarification, we plunge further into detail. (The other partitions can also be out of disk order.)

 First of all, partition programs frequently hide the distinction that follows. MS invented a scheme to allow more partitions, and yet fit the original system too, something usually designated an extended partition. (There is only supposed to be one.) The extended partition, on one level, is one entry in the original partition table. Then, elsewhere on the HD, within this partition, there can be potentially a gazillion partitions, which MS uninformatively calls logical partitions. They didn't use a table with 4, or maybe 100, entries though. Instead, every logical partition has an info section with a place that can be filled in for one further possible partition, or none. Partitions can link to additional partitions indefinitely. Now, if you resize a partition which is not the last one, to obtain another partition, the simplest way to do this links the partitions out of disk order. The last partition points to one that is before it, going by disk order.

 In a way, it doesn't matter, because linux does not care. It doesn't use disk order. But if you do tricky repartioning that changes the linux number of the partitions, Grub will have the wrong numbers, and some of your OSes won't boot. Unfortunately, there is more to this than fixing Grub entries, because Linux (and Windows) still won't boot all the way if its partition number is changed out from under it. If you rework your partitions over and over, it is not unusual to run into this.

 There are low level utilities that (evidently) have never been tested with partitions out of disk order which lose there marbles when they see this, or worse, offer to "fix" it without telling you what is supposedly in error.

---

### Post by kflorek on 2006-09-11
> **Herman said:**
> kflorek,  You'll see a text file named 'default' in /boot/grub. ...

I learned some things from your good explanation about menu.lst, so I thought I'd share something back that I know, thanks for your great info. People like you make these forums interesting and fun.
Regards, Herman :D

 Thanks, Herman. I mean to try that. Your gracious manner is a  greater credit to you than anything I could say. 8)

---

### Post by Psquared on 2006-09-12
> **Herman said:**
> Psquared, 
I'm glad you are happy, that's the most important thing at all times. :)

I was wondering if that was really your Xubuntu menu.lst from /dev/hda4 that you posted in that other thread?

... or was it your /dev/hda2 Kubuntu's menu.lst. It looks like it could be that one, because it has,```
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
```, so it should be your Kubuntu installation's menu.lst, from /dev/hda2, right?

...and yet thinks it's Ubuntu?
```
 ## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

```  Well, I'm  still more than a little puzzled and confused. :confused:

I really think you should check the menu.lst of each operating system and make sure that 'kopt' and 'groot' line for your automagic kernels list has the correct partition number after it. 

If your Ubuntu is really on /dev/hda1, then you should have   # kopt=root=/dev/hda1 ro, and  # groot=(hd0,0), in your Ubuntu's menu.lst, on (hd0,0).

If Kubuntu is really on /dev/hda2, then it's menu.lst should have # kopt=root=/dev/hda2 ro, and  # groot=(hd0,1), in your Kubuntu's menu.lst, on (hd0,1).

If Xubuntu is really on /dev/hda4, then it's menu.lst should have # kopt=root=/dev/hda4 ro, and  # groot=(hd0,3), in your Xubuntu's menu.lst, on (hd0,3).

If you have to edit these entries to make them point to the correct partitions, then it is likely that your /etc/fstab files will need editing too. It's nothing very serious at all, but I have a hunch I know what might be wrong. ... or maybe I'm jumping to the wrong conclusion.
Let me know what you find and I'll help you if you need it. ...Or maybe I'm barking up the wrong tree and nothng more needs to be done.

Just check anyway, oh, and thanks for the sudo fdisk output, those are very often indepensible in sorting out all kinds of problems. I always like to see those, they really are a big help.
Regards, Herman :D


Thanks. Editing menu.lst in Kubuntu doesn't do any good. The Xubuntu install was last even though it is on Hda2. It was the last install to write changes to GRUB on the MBR. So that is the one I had to edit.

See, originally, all I had was Ubuntu on the entire disk. First i split it in half. 80 gig and 80 gigs. The second 80 gigs i split in half again. So I had 3 partitions. Ubuntu was the first installed. Then I installed Kubuntu but when I did I chose Hda4. (Don't ask me why cause I don't know :rolleyes:  ) Then lastly I installed Xubuntu. Hda2 was there ready and waiting so thats what i used.

So, editing menu.lst in Xubuntu on Hda2 did the trick. Its all cleaned up now and makes sense when I boot. Eventually I would like to uninstall these older kernels, but I'll save that for another day.

Thanks all.

---

### Post by Psquared on 2006-09-12
> **Herman said:**
> Psquared, 
I'm glad you are happy, that's the most important thing at all times. :)

I was wondering if that was really your Xubuntu menu.lst from /dev/hda4 that you posted in that other thread?

... or was it your /dev/hda2 Kubuntu's menu.lst. It looks like it could be that one, because it has,```
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
```, so it should be your Kubuntu installation's menu.lst, from /dev/hda2, right?

...and yet thinks it's Ubuntu?
```
 ## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

```  Well, I'm  still more than a little puzzled and confused. :confused:

I really think you should check the menu.lst of each operating system and make sure that 'kopt' and 'groot' line for your automagic kernels list has the correct partition number after it. 

If your Ubuntu is really on /dev/hda1, then you should have   # kopt=root=/dev/hda1 ro, and  # groot=(hd0,0), in your Ubuntu's menu.lst, on (hd0,0).

If Kubuntu is really on /dev/hda2, then it's menu.lst should have # kopt=root=/dev/hda2 ro, and  # groot=(hd0,1), in your Kubuntu's menu.lst, on (hd0,1).

If Xubuntu is really on /dev/hda4, then it's menu.lst should have # kopt=root=/dev/hda4 ro, and  # groot=(hd0,3), in your Xubuntu's menu.lst, on (hd0,3).

If you have to edit these entries to make them point to the correct partitions, then it is likely that your /etc/fstab files will need editing too. It's nothing very serious at all, but I have a hunch I know what might be wrong. ... or maybe I'm jumping to the wrong conclusion.
Let me know what you find and I'll help you if you need it. ...Or maybe I'm barking up the wrong tree and nothng more needs to be done.

Just check anyway, oh, and thanks for the sudo fdisk output, those are very often indepensible in sorting out all kinds of problems. I always like to see those, they really are a big help.
Regards, Herman :D


Thanks. Editing menu.lst in Kubuntu doesn't do any good. The Xubuntu install was last even though it is on Hda2. It was the last install to write changes to GRUB on the MBR. So that is the one I had to edit.

See, originally, all I had was Ubuntu on the entire disk. First i split it in half. 80 gig and 80 gigs. The second 80 gigs i split in half again. So I had 3 partitions. Ubuntu was the first installed. Then I installed Kubuntu but when I did I chose Hda4. (Don't ask me why cause I don't know :rolleyes:  ) Then lastly I installed Xubuntu. Hda2 was there ready and waiting so thats what i used.

So, editing menu.lst in Xubuntu on Hda2 did the trick. Its all cleaned up now and makes sense when I boot. Eventually I would like to uninstall these older kernels, but I'll save that for another day.

The Xubuntu installer renamed Kubuntu, Ubuntu so thats what threw me off. I guess i should file a bug report on that.

Thanks all.

---

### Post by Herman on 2006-09-13
Oh, okay then, I thought it might be something far more complicated, but now that you have explained it more I am satisfied that it's all okay now. Thanks for clearing that up, I'm glad you got it fixed okay.
Regards, Herman :D

---

