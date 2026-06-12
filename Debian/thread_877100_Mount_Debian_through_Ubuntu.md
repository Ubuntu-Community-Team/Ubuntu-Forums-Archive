---
title: "Mount Debian through Ubuntu"
date: 2008-08-01
forum: Debian
---

### Post by BGFG on 2008-08-01
Hi,
Yesterday I installed Debian. I'm having a problem and would like to try to fix it by mounting the filesystem and editing the xserver.xorg file.
In my debian install i used Logical Volume Management. Currently when i mount the drive (the system automounts is actually) I can only see Grub ,Lost and Found and the kernel config file.

Is what i want to do Possible ?

I just came across this in another thread. Is this similar to what i need ?
```

sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o force

```

---

### Post by overdrank on 2008-08-01
Moved :)

---

### Post by BGFG on 2008-08-01
> **overdrank said:**
> Moved :)

Thanks, but in my defense i'm still a beginner :lolflag:
Been in Linux for two months now... Does that count as beginner ? :D

---

### Post by Cypher on 2008-08-01
To fix whatever is broken in Debian, just use any Linux live CD. Ubuntu/Knoppix/Fedora..whatever..boot up and and from the terminal you should be able to mount the Debian partitions and modify files..

---

### Post by unutbu on 2008-08-01
What is the output of 
```

sudo fdisk -l
```
(when you boot from Ubuntu)

---

### Post by BGFG on 2008-08-01
> **unutbu said:**
> What is the output of 
```

sudo fdisk -l
```
(when you boot from Ubuntu)

```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30394   243890797+   5  Extended
/dev/sda5              32       30394   243890766   8e  Linux LVM

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37f23bc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117219265    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14266   114591613+  83  Linux
/dev/sdc2           14267       14593     2626627+   5  Extended
/dev/sdc5           14267       14593     2626596   82  Linux swap / Solaris

```

Seagate 250 gig - Debian ext3
WD 120 Gig - ntfs media dump
WD 120 Gig - Ubuntu ext3

---

### Post by unutbu on 2008-08-01
What happens if you type

```
sudo mkdir /media/Debian
sudo mount /dev/sda5 /media/Debian
```
Look for your debian filesystem inside /media/Debian.

---

### Post by BGFG on 2008-08-01
> **Cypher said:**
> To fix whatever is broken in Debian, just use any Linux live CD. Ubuntu/Knoppix/Fedora..whatever..boot up and and from the terminal you should be able to mount the Debian partitions and modify files..

Sudo Nautilus ?

---

### Post by BGFG on 2008-08-01
> **unutbu said:**
> What happens if you type

```
sudo mkdir /media/Debian
sudo mount /dev/sda5 /media/Debian
```
Look for your debian filesystem inside /media/Debian.

Trying it now..
Output:
```

mount: unknown filesystem type 'LVM2_member'

```

---

### Post by BGFG on 2008-08-01
This is the backstory
```

I've just installed Debian. I installed the nvidia-glx and x-server packages. I have on-board nvidia
I hit ctrl+alt+backspace and my screen went blank.
No response from ctrl+alt+f1 or f5.
Even after a restart, the kernel loads then goes straight to a blank screen. No login prompt or anything.

```

I can't seem to get into the recovery session for debian so i'd like to try to mount the filesystem and manually edit the xserver file and hopefully fix my session.
Since it's the same machine can i replace the Debian file with the working one from Ubuntu ?

---

### Post by unutbu on 2008-08-01
To mount the LVM, try the commands found here:
[http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html](http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html)

Regarding fixing xserver.xorg: Once you have access to the Debian filesystem, you should in theory be able to fix it, but exactly how I do not know. I ran 

```
locate xserver.xorg
```

on my Gutsy machine and found nothing. Is xserver.xorg the Debian equivalent of xorg.conf?
If so, maybe it would work, but I really don't know.
Also, it may be possible that there are backup copies of xserver.xorg in the same directory as xserver.xorg itself. Maybe you can copy one of those into xserver.xorg's place to restore old functionality.

Whatever the case, copy your current xserver.xorg to some backup name like xserver.xorg-broken just to be on the safer side.

---

### Post by BGFG on 2008-08-01
I think i was wrong in posting xserver.xorg it is the same xorg.conf. My mistake. I am currently in a live cd session so i will heck the link and get back here. 
Thanks for the help !

Have to break for a bit (Family machine :) ) back in while...

---

### Post by BGFG on 2008-08-01
this is a little bit annoying. Not too annoying, because i executed a command without knowing exactly how it would behave in a new distribution. But still,
I know it is X, i know the kernel is loading fine, And i know that is is simply a display problem. Because Ubuntu is running perfectly at my max res.

In another thread i was advised to enter the recovery session. Anyone know exactly how to achieve this in debian? i've got two kernels, the standard and one for 'single user mode' which apparently goes to cli. 

I've been searching today and there just doesn't seem to be any concise fixes on the subject. I've come across many bug reports though.

---

### Post by unutbu on 2008-08-01
Single user mode is the same as recovery mode or recovery session. If you have a Debian single-user mode, that is the one the other poster was suggesting you use.

I think you mentioned that you have just installed Debian. Although you will become a more adept user by learning to fix this problem from single-user mode, from a practicality point of view you might want to consider just reinstalling the OS. It may be a whole lot quicker.

---

### Post by BGFG on 2008-08-01
:( Yeah I know, was thinking the same thing. But to install an entire system just because of x.... 
Was hoping to figure it out.
Earlier is used the recovery mode from the install cd and mounted the fs in a shell. Executed startx and was told :
fatal error, no devices found.
I fiddled a bit more and when i ran the regular kernel i was told the x could not start but i at least got the cli. Tried to startx and well.....back to square one.

Can i attempt to re-install the xorg packages using the single user mode ?
Also, 
My problem began when I restarted x after downloading and installing the nvidia driver packages. But in recovery mode i was told that nvidia was not loaded into the kernel. What's the debian version of modprobe ? or the like if it's applicable here ?

---

### Post by unutbu on 2008-08-01
> Can i attempt to re-install the xorg packages using the single user mode ?

Yes, that is possible, but I have a feeling the problem is that your xorg.conf is messed up. And I'm not sure reinstalling those packages will alter xorg.conf. I could be wrong though.

> 
My problem began when I restarted x after downloading and installing the nvidia driver packages. But in recovery mode i was told that nvidia was not loaded into the kernel.
What's the debian version of modprobe ? or the like if it's applicable here ?

modprobe is a common Linux command; Debian probably uses it too. I've never heard of needing to modprobe the nvidia driver. The system should detect that you have an nvidia graphics card and load it itself.

Would you try the following?

Boot into Debian single user mode. This should drop you into a root shell.
What happens when you type
```

sudo dpkg-reconfigure xserver-xorg
```

It should ask you some questions, after you answer them, quit, and try starting X with

```
startx
```

again. If that does not work, type
```

cd /root
lspci -nn > lspci.out
dpkg --get-selections | grep nvidia > dpkg.out
cp /etc/X11/xorg.conf xorg.conf-Debian.out
ls -l /etc/X11 > ls.out
reboot

```
Then boot into Ubuntu. Open a terminal and type
```

cp /etc/X11/xorg.conf xorg.conf-Ubuntu

```
Now mount your Debian partition from within Ubuntu at /media/Debian. Then type
```

cp /media/Debian/root/*.out ~
```

Then post as attachments

lspci.out, dpkg.out, xorg.conf-Debian.out, ls.out and xorg.conf-Ubuntu.

---

### Post by BGFG on 2008-08-02
Thanks so much for all your Help man....

dpkg-reconfigure runs into a wall at the point of selecting colour depth. tried 8 16 and 24 bit but i get an error saying that i'm trying to copy to the xorg.conf and lose access to the reconfigure window. Even after i say no to the earlier options to save info to the file.

As for the other commands... I still can't mount my LVM partitions so i'm screwed.

I think you were right about the re-install.
Neer hath this one loved Ubuntu than this one does today..... 
Maybe i'll just hold on for 'lenny'. etch was running slower that hardy anyways :)
Ok Ok now i'm just being petulant.... Arrrgh :)

---

