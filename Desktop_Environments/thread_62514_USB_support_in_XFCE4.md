---
title: "USB support in XFCE4"
date: 2005-09-04
forum: Desktop Environments
---

### Post by celluloid on 2005-09-04
Hi guys, firstly I'd like to say that Ubuntu is a fantastic distro. I've been using it for about a week now and have apt-get updated to Breezy (with some repository connection problems, that however seem to be sorted now).

Any how, enough praise for now.  :) 
My question, I'm running a fairly old box. 700mhz, 128mb ram, 4 gig HDD + 812mb HDD (Swap). 
GNOME is fairly slow, although stable, I apt-'got' XFCE4. Which runs fairly nice on these specs. I have an Iriver H300 series mp3 player which is automatically detected on GNOME and shown on the desktop, it's located in /etc/media/GRANT H300
However in XFCE4 it is not detected? I have looked in the previous directory incase it needed to be mounted, but no luck.

I'm sorry if this has been answered before, I used search to no avail and google with no luck. If i can sort out this problem I will gladly switch to XFCE4 as it seems to have a good compromise between useability + speed.

I'm sure someone will be able to help me out here, seems like a great community and I'm pleased to be a part of it.

Thankyou in advance.
Grant.

---

### Post by celluloid on 2005-09-05
Ok well, I am in XFCE4 right now, and using the filebrowser it appears as though GRANT H300 has been detected in etc/media/. However clicking of this does not show anything but a blank screen, almost as if the entire device is empty.

Not exactly sure where to go from here.

---

### Post by smeager on 2005-09-05
Ok this is what I had to do to use to get any  usb device to work. (But you do not have write permissions out side of root). You can copy any file to it using the terminal command:  sudo cp *FILENAME.PNG* /media/flash (or whatever you call it)

Open a terminal and type the following

smeager@skulboxx:~$ sudo mkdir /media/flash
smeager@skulboxx:~$ mount /dev/sdb1 /media/flash/
mount: only root can do that
smeager@skulboxx:~$ sudo mount /dev/sdb1 /media/flash/

You can make any directory you want anf then mount the device to it.

ie: $ sudo mkdir /media/Iriver H300
ie: $ sudo mount /dev/sdb($) /media/Iriver H300

It should show up as a normal usb device. 

I hope this helps you a little. I will continue looking for a better way of doing this but at least you can do something now.

---

### Post by celluloid on 2005-09-05
[QUOTE=smeager]Ok this is what I had to do to use to get any  usb device to work. (But you do not have write permissions out side of root). You can copy any file to it using the terminal command:  sudo cp *FILENAME.PNG* /media/flash (or whatever you call it)

Open a terminal and type the following

smeager@skulboxx:~$ sudo mkdir /media/flash
smeager@skulboxx:~$ mount /dev/sdb1 /media/flash/
mount: only root can do that
smeager@skulboxx:~$ sudo mount /dev/sdb1 /media/flash/

You can make any directory you want anf then mount the device to it.

ie: $ sudo mkdir /media/Iriver H300
ie: $ sudo mount /dev/sdb($) /media/Iriver H300

It should show up as a normal usb device. 

I hope this helps you a little. I will continue looking for a better way of doing this but at least you can do something now.[/QUOTE]
 Wow, Thankyou very much Smeager.
Got it to work after a few tries, turns out that instead of /dev/sdb1 i needed to mount /dev/sda1
Now, is this change permanent or must i mount the device like this after every boot or connection of the device?

---

### Post by recce101 on 2005-09-05
I'm just slightly less of a newbie than you, and though I don't use an MP3, I have played with XFCE and device mounting quite a bit the last couple of weeks and might be able to help you in this area.

First, on my XFCE panel I created custom icons for Root Terminal and Root File Manager WHICH I USE A LOT. Right-click on one of the default icons, choose Launcher, click Add, then fill in the properties for the custom icon you want. Take Root Terminal as an example. Click the Other Icon dropdown and pick the icon display you like, such as Terminal (this will give you two identical-looking icons, which you can differentiate with different tooltip entries). Leave the box under Other Icon blank, put "gksudo xfterm4" (no quotes) in the Command box, put "Root Terminal" in the Tooltip box, clear the three small boxes, then close. The first time you click the new icon you'll be asked for a password (use your user password, since you probably don't have a root password). Then you'll see a terminal screen with the root prompt. Very handy, saves a lot of sudo-ing. A custom icon for Root File Manager would need "gksudo rox" in the Command box. An icon for Synaptic, which has to be run by root, would use "gksudo synaptic." Lots of possibilities here.

You should be able to edit your /etc/fstab file and get the mp3 to mount automatically at start if it's connected. Might need to play around with the options some and do a few reboots to get it working consistently. Use the "fdisk -l" command after booting to see what's been automatically loaded. If you have to manually mount, issue just the "mount" command to see what options are listed, then edit your /etc/fstab accordingly. There are probably more sophisticated methods, but that worked for me in gettng my usb external hard drive to mount automatically at start.

I think XFCE is terrific. Fast, stable, easy for my old-guy brain to figure out.

---

### Post by celluloid on 2005-09-05
[QUOTE=recce101]I'm just slightly less of a newbie than you, and though I don't use an MP3, I have played with XFCE and device mounting quite a bit the last couple of weeks and might be able to help you in this area.

First, on my XFCE panel I created custom icons for Root Terminal and Root File Manager WHICH I USE A LOT. Right-click on one of the default icons, choose Launcher, click Add, then fill in the properties for the custom icon you want. Take Root Terminal as an example. Click the Other Icon dropdown and pick the icon display you like, such as Terminal (this will give you two identical-looking icons, which you can differentiate with different tooltip entries). Leave the box under Other Icon blank, put "gksudo xfterm4" (no quotes) in the Command box, put "Root Terminal" in the Tooltip box, clear the three small boxes, then close. The first time you click the new icon you'll be asked for a password (use your user password, since you probably don't have a root password). Then you'll see a terminal screen with the root prompt. Very handy, saves a lot of sudo-ing. A custom icon for Root File Manager would need "gksudo rox" in the Command box. An icon for Synaptic, which has to be run by root, would use "gksudo synaptic." Lots of possibilities here.

You should be able to edit your /etc/fstab file and get the mp3 to mount automatically at start if it's connected. Might need to play around with the options some and do a few reboots to get it working consistently. Use the "fdisk -l" command after booting to see what's been automatically loaded. If you have to manually mount, issue just the "mount" command to see what options are listed, then edit your /etc/fstab accordingly. There are probably more sophisticated methods, but that worked for me in gettng my usb external hard drive to mount automatically at start.

I think XFCE is terrific. Fast, stable, easy for my old-guy brain to figure out.[/QUOTE]
 Thanks reece101.

I've been using linux on and off for a while but only for basic computing and never really going into depth and learning much, just floating around between different distro's due to my old computer have never really been able to dive right in.

XFCE seems great, faster than GNOME and fairly stable. 
My mp3 uses a removable device driver so it is detected as a removeable hdd in windows, GNOME etc for "drag + drop" usage, which makes it alot more compatible as i don't need to use drivers. I'll have a go at etting the /etc/fstab shortly.

Thanks very much for your support.

---

### Post by celluloid on 2005-09-05
[QUOTE=recce101]I'm just slightly less of a newbie than you, and though I don't use an MP3, I have played with XFCE and device mounting quite a bit the last couple of weeks and might be able to help you in this area.

First, on my XFCE panel I created custom icons for Root Terminal and Root File Manager WHICH I USE A LOT. Right-click on one of the default icons, choose Launcher, click Add, then fill in the properties for the custom icon you want. Take Root Terminal as an example. Click the Other Icon dropdown and pick the icon display you like, such as Terminal (this will give you two identical-looking icons, which you can differentiate with different tooltip entries). Leave the box under Other Icon blank, put "gksudo xfterm4" (no quotes) in the Command box, put "Root Terminal" in the Tooltip box, clear the three small boxes, then close. The first time you click the new icon you'll be asked for a password (use your user password, since you probably don't have a root password). Then you'll see a terminal screen with the root prompt. Very handy, saves a lot of sudo-ing. A custom icon for Root File Manager would need "gksudo rox" in the Command box. An icon for Synaptic, which has to be run by root, would use "gksudo synaptic." Lots of possibilities here.

You should be able to edit your /etc/fstab file and get the mp3 to mount automatically at start if it's connected. Might need to play around with the options some and do a few reboots to get it working consistently. Use the "fdisk -l" command after booting to see what's been automatically loaded. If you have to manually mount, issue just the "mount" command to see what options are listed, then edit your /etc/fstab accordingly. There are probably more sophisticated methods, but that worked for me in gettng my usb external hard drive to mount automatically at start.

I think XFCE is terrific. Fast, stable, easy for my old-guy brain to figure out.[/QUOTE]


I'm not exactly sure what I am supposed to put in my /etc/fstab file.
I will include my current /etc/fstab/ file and the output of "fdisk -l" in hopes that someone can inform me.

grant@ubuntu:~$ fdisk -l

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2431    19526976    c  W95 FAT32 (LBA)

and the /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any ideas as to what to add to this would be great.
I am pretty sure i would follow the formula of /dev/sda1 then /media/h300. but i am not sure what to put for "auto", "rw, user....." sections. 

I am looking for this device to be loaded on boot. :)

Grant.

---

### Post by smeager on 2005-09-05
If you want to make the change to fstab it should look something like this:

proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdc1 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
*/dev/sda1 /media/h300 vfat auto rw,user,noauto 0 0 * 

It should work that way. (vfat is the filesystem type ie fat32, fat16 ect.)

---

### Post by celluloid on 2005-09-06
[QUOTE=smeager]If you want to make the change to fstab it should look something like this:

proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdc1 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
*/dev/sda1 /media/h300 vfat auto rw,user,noauto 0 0 * 

It should work that way. (vfat is the filesystem type ie fat32, fat16 ect.)[/QUOTE]
 This allows the device to be mounted through going into rox and clicking it to open it. (which previously couldn't be done, had to be mounted manually through the terminal)

However I still cannot figure out how to get the device to be mounted on boot (it's connected at boot 99% of the time) Is there still some extra feilds i'm missing?

EDIT: 
I removed "auto" after vfat and changed "noauto" to "auto"
Now upon booting i get a message saying.
Mount: Special Device /dev/sda1 does not exist.

Device is still mountable via clicking in rox but not upon boot. Very confused.

---

### Post by kblood on 2005-09-06
Well, I think you are all going the hard way about it.

Check here:
[https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport)

More specifically, at the end:
>  One of the useful features that running Gnome provides is the 'auto-magical' mounting of removable media, like CD's and USB drives. However, you can very easily have this feature whilst you use the superb XFCE4 Desktop Environment.

    * Open a terminal window and run 'gnome-volume-manager&'. This will start gnome-volume-manager and run it in the background.
    * Next time you quit XFCE4, select 'Save session for future logins'. This will ensure that gnome-volme-manager starts each time you start xfce.
    * Now plugin your favourite USB drive or CDRom and find it magically mounted in /media/xxxxx.

Note, that this won't bring up an icon onto your desktop as it would in Gnome as XFCE doesn't have support for desktop icons. However nice things, like the automatic importing of photos from memory cards and playing of audio CDs does occur.


This should make you all pretty happy.

---

### Post by celluloid on 2005-09-06
[QUOTE=kblood]Well, I think you are all going the hard way about it.

Check here:
[https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport)

More specifically, at the end:


This should make you all pretty happy.[/QUOTE]
 Wow, thanks heaps. Seems to just what i was after, however upon running 'gnome-volume-manager&' the script does not seem to stop?

ends on
manager.c/1250: mount_all: mounting /dev/hda1
manager.c/659: /org/freedesktop/Hal/devices/block_3_1 already mounted, not mounting again
manager.c/1250: mount_all: mounting /dev/hdc1
Warning: device /dev/hdc1 is already handled by /etc/fstab, supplied label is ignored
mount: mount point none does not exist
manager.c/1056: is_mounted property of /org/freedesktop/Hal/devices/block_E8CD-0
A5A changed to true

And then a blinking cursor, just wondering what to do now and if closing the terminal will cancel/undo this?

EDIT: Never mind, i'm just silly haha, just pressed enter and it finished.
Thanks heaps.

---

### Post by kblood on 2005-09-06
I think you forgot to add the & at the end of the line.
That makes it run in the background, as it's meant to run. It's a program that is supposed to be running at all times, checking for new cds or usb drives and mounting them automatically.

So close that now and run it with the &.

I am not sure, though, what your fstab file should have now if you are going to be running that.

---

### Post by celluloid on 2005-09-06
[QUOTE=kblood]I think you forgot to add the & at the end of the line.
That makes it run in the background, as it's meant to run. It's a program that is supposed to be running at all times, checking for new cds or usb drives and mounting them automatically.

So close that now and run it with the &.

I am not sure, though, what your fstab file should have now if you are going to be running that.[/QUOTE]
 Excellent, rebooted and works fine. 
Thanks so much for your help all, My ubuntu is starting to work nicely.
As i work through the problems, the 'fun/excitement' level seems to go down though. :P 
As damn fustrating it was with these little problems, it added a level of risk and discovery hehe, i bet there will be more to do yet.

Thanks all.
Grant.

---

