---
title: "Make second Ubuntu Partion bootable"
date: 2009-03-12
forum: General Help
---

### Post by Weidbrewer on 2009-03-12
I installed Ubuntu Server 64 8.10 on a drive to try it out, and cloned over the Ubuntu 32 8.10 partition from the old setup.  Currently, I can boot in to 32 just fine, but can't figure out how to add the 64 to GRUB and make it bootable.  Any suggestions?

---

### Post by Nano_ext3 on 2009-03-12
I don't suggest "cloning" over a hard drive, especially with dd.  dd is a nice tool, but should only be used to copy to a partition if you messed up the current one.  Lets say you dd a partition when you get it setup.  Theoretically, as long as you dont re-install over, or reinstall the OS on that partition you can dd the orig. partition back onto the busted partition (the same orig. partition that you may have messed up, in our fictional world here).  It is always best to fresh install, rather than clone.


As long as the second linux OS is on a separate partition, and formatted as ext3 (or ext4 if you can), complete the install and you should be able to choose either.  Not sure why you are having an issue.  

You can easily dual boot 2 different distributions on one hard disk,, you dont need to remove the MBR (of previous distros)... just install it from the cd,, but you have to remember the partitions which you are getting rid of...I mean...in this case,, you will be having 2 root partions..

In each case you need to specify "/" or root level when installing.  Always make sure for dual boot, each root partition is on a SEPERATE partition on the disk.  So, mountpoint is "/", partition type typically is "ext3."  

Let us say you installed the second linux OS to sda6, then it would be this in your /boot/grub/menu.lst file:

Slackware in sda6 known to Grub as (hd0,5)
root (hd0,5)
chainloader +1


If one installs say 10 distros one has 10 boot loaders installed by default but there is only one MBR so one can only nominate any of the 10 boot loader to take over that position. The remaining 9 boot loader should therefore be installed in their respective root partitions. Then the last Linux will be able to pick out all of them for boot.  The Debian family, to which Ubuntu belong, is pretty good in automatically arranging multi-booting.  

Let it be noted, that depending on your distro's , you may have more than one kernel version of each respective distro in you list, you want to keep at least 2 in this list of any distro, but they can be edited or commented out by using "#" in front of a line in /boot/grub/menu.lst


Hope this helps!

Cheers,

-Nano

---

### Post by Weidbrewer on 2009-03-12
Normally, that is what I've experienced - installing another distro/verison/etc updates grub...but that didn't happen here.  Let's just go from the assumption that I did something wrong with the install....how do I fix it?

All I have in my menu.lst is this:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro quiet splash vga=795 apci=off
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

These are the grub options from my original install that I cloned over.

Here is my fdisk:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1186     9526513+  83  Linux
/dev/sdc2            1187        3649    19784047+   5  Extended
/dev/sdc5            1187        3345    17342136   83  Linux
/dev/sdc6            3346        3649     2441848+  82  Linux swap / Solaris

/dev/sdc1 contains the OS listed above.  /dev/sdc5 contains the 64 bit version that I would like to add to my boot options.  How do I edit the menu.lst to add this?

Thanks!

---

### Post by Weidbrewer on 2009-03-15
Anyone got any idea?

---

### Post by meierfra. on 2009-03-15
I suggest to install grub to the boot sector of your 64 bit partition and then chainload the boot sector:

Boot to your 32-bit ubuntu.

```
sudo grub
```
and at the grub prompt:

```

device (hd0) /dev/sdc
root (hd0,4)
setup (hd0,4)
quit
```

```
gksudo gedit /boot/grub/menu.lst
```

And add this to the end of the file:

title Ubuntu 64
root (hd0,4)
chainloader +1

---

### Post by Weidbrewer on 2009-03-16
That makes perfect sense.  I'll give that a try after work and see if it does the job.  Thanks for the pointer.

---

### Post by Weidbrewer on 2009-03-16
Excellent...we are now getting somewhere.   Now, my menu.lst looks like this:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro quiet splash vga=795 apci=off
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Ubuntu Server 64
root		(hd0,4)
chainloader +1
```

With this, I can boot in to 64, which for all sakes a purposes is mission accomplished - however, there is a littl clean-up that I would like to do, if possible.

When I get to GRUB and select "Ubuntu Server 64," it takes me to the GRUB menu for the other partition, which looks like this in the menu.lst file:

```

title		Ubuntu Server 64 8.10, kernel 2.6.27-7-generic
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8d5ff14e-793b-43eb-9e0c-47c246987318 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu Server 64 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8d5ff14e-793b-43eb-9e0c-47c246987318 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro quiet splash vga=795 apci=off 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Now, this menu displays exactly how I'd like it to - both main installations and their recovery modes list on the same menu.  Is there anything that I can modify so that I don't go through two menus, and can have everything display together?  Without a reinstall, can I have it look at this partition for GRUB first?

Like I said, I can get where I need to now, so if the above is too tricky, I can deal with that.   Thanks again for all the help.

---

### Post by meierfra. on 2009-03-16
> Without a reinstall, can I have it look at this partition for GRUB first?
Yes

```

sudo grub
device (hd0) /dev/sdc
root (hd0,0)
setup  (hd0,0)
root (hd0,4)
setup (hd0)
```


and add 

title Ubuntu 32
root (hd0,0)
chainloader +1

to the Ubuntu 64 menu.lst
(Make sure put  this item below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it will be removed during the next kernel update.)



> Is there anything that I can modify so that I don't go through two menus, and can have everything display together?

You can do that, (just copy and past the entries from the one menu to the other)  but then you will have to edit your Ubuntu 64 menu.lst after each Ubuntu 32 kernel update. Instead I recommend to just hide the second Grub Menu:

Edit your Ubuntu 32 menu.lst as follows: 

Change

timeout 10  to timeout 2

and

#hiddenmenu to hiddenmenu

(This hides the Ubuntu 32 grub menu. So only do this if you  already carried out  the first part of my post)

---

### Post by Weidbrewer on 2009-03-17
Hmmm...following your instructions in the first part, I get stuck here:

```
grub> setup  (hd0,0)
setup  (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

---

### Post by meierfra. on 2009-03-17
Did you notice my correction?  I had left out  "device (hd0) /dev/sdc"  as the first command at the grub prompt.

---

### Post by meierfra. on 2009-03-17
Oops, I just noticed that I had  messed up the correction. (the extra line was in the wrong place) But it is correct now.

---

### Post by Weidbrewer on 2009-03-17
Thank you for the corrections...I'm thinking the error is on my end.  Here is what I've been getting (and stuck in the same place):

```
weidbrewer@deus-ex:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/sdc
device (hd0) /dev/sdc
grub> root (hd0,0)
root (hd0,0)
grub> setup  (hd0,0)
setup  (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> 


```

---

### Post by meierfra. on 2009-03-17
maybe your device names have changed. Could you post the output of "sudo fdisk -lu"?

Even if the device names have changed,  the following should work: At the grub prompt:

```
find /boot/grub/stage1
```
(1 is the number one, not a lower case L)

This should return (hdX,0) and (hdX,4), where X is some number. Then, still at the grub prompt:


```
root (hdX,0)
setup  (hdX,0)
root (hdX,4)
setup (hdX)
quit

```

---

### Post by Weidbrewer on 2009-03-17
We are now in a good news, bad news, freakin' terrible news situation.

God News:  Boots like a champ to the 64 menu, with all the rights and privileges there-of.

Bad News:  If I select the 32-bit option, it says that the disk does not exist.

Freakin' Terrible News:  I wnet back and changed the 32-bit menu.lst to #hidden menu, and reset the timeout.   Still skips past it to the 64 bit menu.  The 32-bit partition is the every day one that servers the other front ends of my house, and now I can't access it.

Crap.


Additional news:  on a few of the reboots, my device points changes.  Seems to have stabled off and my drives/partitions are auto mounting as they should.  Weird.

Per your request:

```
weidbrewer@deus-ex:~$ sudo fdisk -lu
[sudo] password for weidbrewer: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002d8e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953520064   976760001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52716566

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c5e7fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    39873329    19936633+  83  Linux

Disk /dev/sdd: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x037b037a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    19053089     9526513+  83  Linux
/dev/sdd2        19053090    58621184    19784047+   5  Extended
/dev/sdd5        19053153    53737424    17342136   83  Linux
/dev/sdd6        53737488    58621184     2441848+  82  Linux swap / Solaris

```


Hopefully you have some cure to whatever I screwed up.  Now, I gotta get some sleep.  Thanks for the help.

---

### Post by meierfra. on 2009-03-17
> I went back and changed the 32-bit menu.lst to #hidden menu, and reset the timeout. Still skips past it to the 64 bit menu.

It does not skip  past 32-bit menu.  The 64-bit menu is now the first grub menu. I thought that's what you wanted then you said "Without a reinstall, can I have it look at this partition for GRUB first?"


> If I select the 32-bit option, it says that the disk does not exist.


Sound like you used the wrong entry in the 64-bit menu.lst

It has to be

title Ubuntu 32
root (hd0,0)
chainloader +1

Maybe you used (hd4,0), since that's what "find /boot/grub/stage1" returned?  That's one of the confusing things of grub. The grub at boot up sees the hard drive in a different order than the grub  shell you get from "sudo grub"


Or are you trying to boot some of the other Ubuntu 32 items on the 64-bit grub menu? They won't work since they use "root (hd0,3)". I suggest to delete whose items. Or if you want to use them, change "root (hd0,3)" to "root (hd0,0)"

If you still can't boot into the  32-bit Ubuntu after changing the Ubuntu 32 item in the Ubuntu 64 menu.lst, try  this


```

find /boot/grub/stage1
root (hdX,0)
setup  (hdX,0)
quit

```
at the grub prompt again.

---

### Post by Weidbrewer on 2009-03-17
> It does not skip past 32-bit menu. The 64-bit menu is now the first grub menu. I thought that's what you wanted then you said "Without a reinstall, can I have it look at this partition for GRUB first?"

I guess that I misunderstood what that was supposed to accomplish.

> Sound like you used the wrong entry in the 64-bit menu.lst

Nope...I cut and pasted exactly what you had.

> 
title		Ubuntu Server 64 8.10, kernel 2.6.27-7-generic
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8d5ff14e-793b-43eb-9e0c-47c246987318 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu Server 64 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8d5ff14e-793b-43eb-9e0c-47c246987318 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8d5ff14e-793b-43eb-9e0c-47c246987318
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro quiet splash vga=795 apci=off 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdd1)
root		(hd3,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title Ubuntu 32
root (hd0,0)
chainloader +1


I didn't change anything on the 32 items...Here is whatthe command returns:

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd3,0)
 (hd3,4)

```


(Although, when I ran that last night, I would have sworn it was (hd2,0)....any reason things seem to keep changing around every time I run them?)

---

### Post by Weidbrewer on 2009-03-17
Okay, I redid the grub part about for (hd3,4), and now I can boot back in to my 32 partion.

In the process, I see where the breakdown in communication was.  Here is my boot menu (with numbers added for clarity):

```
[LIST=1]
[*]Ubuntu Server 64 8.10, kernel 2.6.27-7-generic
[*]Ubuntu Server 64 8.10, kernel 2.6.27-7-generic (recovery mode)
[*]Ubuntu 8.10, memtest86+

Other operating systems:

[*]Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (on /dev/sdd1)
[*]Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/
[*]Ubuntu 8.10, memtest86+ (on /dev/sdd1)
[*]Ubuntu 32
[/LIST]
```

1, 2 and 3 work fine.

4, 5 and 6 do not, and these were the ones I really wanted to make work.

After the above update, 7 works - but takes me to a second boot menu, the reverse of what we had before with the 64-bit menu.   What I was trying to do was to have all options on one menu.  Rereading what you said, it seems that this is something that might be more trouble than it is worth...so, since I have it at least working now, I'll leave well enough alone.


Thanks for the help!

---

### Post by meierfra. on 2009-03-17
If you want 4,5, and 6 to works change them like this

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.

title Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (on /dev/sdd1)
root (hd0,0)
kernel /vmlinuz root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro quiet splash vga=795 apci=off
initrd /initrd.img



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title Ubuntu Desktop 32 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdd1)
root (hd0,0)
kernel /vmlinuz root=UUID=bb23a3a7-1e09-4f5c-9bdc-96ac5de4abc8 ro single
initrd initrd.img



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd1.
title Ubuntu 8.10, memtest86+ (on /dev/sdd1)
root (hd0,0)
kernel /boot/memtest86+.bin

Well,  I would leave out the last one. No reason to have  two memtests on the Grub menu.


So change "root (hd3,0)" to "root (hd0,0)". Replace the full paths to the kernel and initrd by the symlinks (/vmlinuz and /initrd.img) (If you use the symlinks you won't have to  edit your menu.lst after kernel updates)
Also deleted "savedefault" and "boot". They don't cause any harm, but they aren't needed either.

---

### Post by Weidbrewer on 2009-03-17
Sure, I'll give that a whirl as soon as a few things finish installing.

---

### Post by Weidbrewer on 2009-03-18
That did the trick.  Awesome.  Once again, thanks for the help!

---

### Post by meierfra. on 2009-03-18
> That did the trick. Awesome. Once again, thanks for the help!

Glad you got it to work.  Have fun with all  your Ubuntu's

---

### Post by Weidbrewer on 2009-03-18
Isn't that why we do this?  Now I get to have fun with migrating over MythTV, which is always fun!  WEEEEEEEEEEEEEE! (Actually, I'm almost done with that now.)

---

