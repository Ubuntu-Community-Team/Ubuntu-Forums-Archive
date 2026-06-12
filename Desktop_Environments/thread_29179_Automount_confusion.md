---
title: "Automount confusion"
date: 2005-04-23
forum: Desktop Environments
---

### Post by kevin1 on 2005-04-23
I was impressed by the smooth installation of V5.04 (except for sound, which will be the subject of another post), but have since been struggling to make sense of configuration and automount for removable media.

Relevant lines from /etc/fstab:

/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hdb4	/media/zip	vfat	rw,user,noauto	0	0

Although dmesg includes the line: 'hdb: IOMEGA ZIP 250 ATAPI, ATAPI FLOPPY drive' there was originally no zip entry in fstab so I added the zip entry by trial-and-error. 

Under /media in the Nautilus tree there are folders 'cdrom0' and 'cdrom1' and also a link 'cdrom' which has '/media/cdrom0' as its target. Similarly there is a folder 'floppy0' and a link 'floppy' with target '/media/floppy0'.
For the zip drive there is simply a folder 'zip', with no link. I am not sure of the purpose of the links and why only certain folders have them.

CDs and DVDs automount and can be ejected via a right-click on the desktop icon or in Nautilus, but not via the eject buttons on the drives unless already unmounted via the console (no big deal).

If the machine is booted without a zip disk inserted, automount does not work, and attempts to mount via the console result in the message:

:~$ mount /media/zip
mount: special device /dev/hdb4 does not exist

It appears that zip is regarded as a hard drive, so must be present at boot.

After booting with a zip disk inserted, automount still does not work, but the disk may be mounted via the console.
On attempting to eject via a right-click on the desktop icon or in Nautilus the disk is unmounted, but fails to eject with the message: 'Unable to eject media', with details: 'eject: unable to open /dev/hdb4'. The disk may be ejected via the eject button on the drive.

The floppy drive does not automount. Once the floppy has been mounted via the console, it may be unmounted via a right-click on the desktop icon or in Nautilus.

During online searches to resolve these issues I have seen much conflicting advice. Some refers to autofs configuration files such as /etc/auto.master and /etc/auto.floppy, but these do not appear to exist on my system.
Others refer mysteriously to 'HAL' without much explanation.


I would be very grateful for any advice on how to configure the system so that I can use the zip and floppy drives in the same way as the CD & DVD drives.

Thanks,

Kevin

---

### Post by Nis on 2005-04-24
Avoid any talk about autofs, Supermount, or magicdev.  Those are old ways of doing automatic mounting of filesystems.  What does it now is a combination of udev (device manager), hotplug (notifies when new devices are connected), HAL (hardware abstraction layer, allows the next part to work), and gnome-volume-manager (does the actual automouting).
Try removing the zip line from your /etc/fstab and seeing if the drive is auto-mounted when you insert it.  A good idea is to 'tail -f /var/log/messages' in a console as you do this and see what messages you get.  If you get any about not being able to create a certain device then that might be the problem and we'll work at it some more.

Floppy drives have never auto-mounted for me so I guess gnome-volume-manager just doesn't know how to work that yet.

Optical media do not eject by buttons on the drives unless unmounted.  This a design decision in the Linux kernel.  This prevents the media from being ejected while a read is taking place.  Bad things happen if you do this as evidenced in Windows.

Don't worry about the link thing in /media.

Let's see what happens.

---

### Post by kevin1 on 2005-04-24
Thanks for your reply Nis,

I removed the zip entry from /etc/fstab, rebooted and had 'tail -f /var/log/messages' running in a root console as I inserted a zip disk. The disk did not automount, nor were any messages generated in the root console. This was the reason for my experimenting with /etc/fstab.

'ps -e' includes the following lines which may be relevant:

  PID TTY          TIME CMD

 1134 ?        00:00:00 udevd
 6554 ?        00:00:00 hald
 7134 ?        00:00:00 gnome-volume-ma
 7145 ?        00:00:00 gnome-vfs-daemo

This would seem to suggest that three of the four software components are running.
I think 'hotplug' must also be ok since a USB memory stick automounts without problems (generating several lines in /var/log/messages).

If I try a manual mount:

:~$ mount /media/zip
mount: can't find /media/zip in /etc/fstab or /etc/mtab

'cat /etc/mtab' shows:

/dev/hda10 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda1 /mnt/dos vfat rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw

I observe that there is no entry here for zip, but there is one for USB although the memory stick was unmounted before executing the command.

I'm still confused. 

If you have any advice on what I should try next I would be grateful.

Thanks,

Kevin

---

### Post by AndersAA on 2005-04-24
mtab shows filesystems that are mounted, which your "zip" entry of course wont be after an error message.

try "fdisk -l" as root if you want to see which harddrives/zip drives you can mount, it'll most likely be listed there.

---

### Post by neighborlee on 2005-06-12
[QUOTE=Nis]Avoid any talk about autofs, Supermount, or magicdev.  Those are old ways of doing automatic mounting of filesystems.  

Optical media do not eject by buttons on the drives unless unmounted.  This a design decision in the Linux kernel.  This prevents the media from being ejected while a read is taking place.  Bad things happen if you do this as evidenced in Windows.

Don't worry about the link thing in /media.

Let's see what happens.[/QUOTE]

bad things happen if you try to eject via button on drive as is evidenced by windows ???..i've used windows for AGES and I've never had any problems so please refine your statement with some facts...

You would also need to convince not only suse and mandriva, but also knoppix, linspire, xandros, mepis and im sure many other distros that have this functionality built in ( and fedora it can be added by rpm ), that this is bad design.   We must remember that while unix zealots might not care about umount working via eject button , that windows users have learned to enjoy the convenience this offers and since I have never had issues with it in all my years of windows use ( or mandriva or whatever) then I highly suspect its a non-issue.

cheers
nl

---

### Post by bjunix on 2005-06-16
i never had any problems concerning the eject button and windows. ok i actually had. but this was back when win95 was state of the windows art.
with win2k or even winxp i never had any interferences with the windows kernel. so the linux kernel should be able to compete with mircosoft patch work.

---

### Post by neighborlee on 2005-06-16
[QUOTE=bjunix]i never had any problems concerning the eject button and windows. ok i actually had. but this was back when win95 was state of the windows art.
with win2k or even winxp i never had any interferences with the windows kernel. so the linux kernel should be able to compete with mircosoft patch work.[/QUOTE]

well i'm glad im not the only debian user that understands this LOL...I'm going to mess with supermount-ng and see if I can get it working here in conjunction with kernel and get any patches for ubuntu ...

however IF any developer/user is working on gettting eject button to work or has already done it please let me know so I dont duplicate work

cheers
nl

---

### Post by AndersAA on 2005-06-16
it's not "bad" because it doesn't eject, it's bad because (and you can try this in fairly new windows version) if you open a file on cd and press eject the program with the file open will tend to do bad things (ie crash).

---

### Post by neighborlee on 2005-06-16
[QUOTE=AndersAA]it's not "bad" because it doesn't eject, it's bad because (and you can try this in fairly new windows version) if you open a file on cd and press eject the program with the file open will tend to do bad things (ie crash).[/QUOTE]

well no offense but WHO is dumb enough to do that ?

I mean are we worried about the least absolute case scenario of user idiocy , to the point that we ignore userfriendly behavior that windows and MANY other linux distro say  is 'just okay' ?

if so we're fooling ourselves and not thinking rationally.

cheers
nl

---

### Post by AndersAA on 2005-06-16
[QUOTE=neighborlee]well no offense but WHO is dumb enough to do that ?[/quote]
uhm... an incredible amount of people.
Also if you work on many documents at the same time you may do it without realizing it.  Which is especially difficult in .edu situations, where computers are more shared.  And someone can take a cd and leave, and come back to a computer that doesn't work.

[QUOTE=neighborlee]I mean are we worried about the least absolute case scenario of user idiocy , to the point that we ignore userfriendly behavior that windows and MANY other linux distro say  is 'just okay' ?

if so we're fooling ourselves and not thinking rationally.

cheers
nl[/QUOTE]

Whats so user unfriendly about right clicking on a icon on your desktop and clicking eject?

---

### Post by neighborlee on 2005-06-16
[QUOTE=AndersAA]uhm... an incredible amount of people.
Also if you work on many documents at the same time you may do it without realizing it.  Which is especially difficult in .edu situations, where computers are more shared.  And someone can take a cd and leave, and come back to a computer that doesn't work.



Whats so user unfriendly about right clicking on a icon on your desktop and clicking eject?[/QUOTE]

I guess your arguement is convincing for those in a networking environment but really forcing someone ( with no option I mean ) to do archaic things like right clicking a desktop icon and going eject is at least IMO unnecessarily causing complexity to something that doesn't need to be for home users...so are you saying that all the other distros that do this are somehow going against the grain of wisdom in the linux world ?

I must use windows and linux both and I can't tell you how much less hastle is involved when I just click eject button , and besides..since when is user friendly more appropriate when it takes twice as much input from a user to perform a specific function ? ;-)

;-)

cheers
nl

---

### Post by RastaMahata on 2005-06-16
You wouldnt believe the stories from technical support...

(The user brought the PC to the technical center)
Support: Hello. How may I help you
User: I cant Install Microsoft office. It seems the PC you sold me is broken or something...
Support: Well, what happens when you try to install it?
User: Nothing... actually, the cd thingy sounds a bit weird...
Support: Well, let's see, maybe the CD drive has a bit of dust or maybe...
(The technician opens the cd drive)
Support: ...
User: What?
Support: There are two cds in this drive
User: well, DUH!
Support: Excuse me, but why is the Office cd on top of the windows cd?
User: Well, the office cd says "It runs on windows 98", so...

Yes, this actually a true story... As true as another one of a user thinking that the mouse was used on top of the monitor, and another one where the user tried to use the mouse with his foot...

---

### Post by neighborlee on 2005-06-17
[QUOTE=RastaMahata]You wouldnt believe the stories from technical support...

(The user brought the PC to the technical center)
Support: Hello. How may I help you
User: I cant Install Microsoft office. It seems the PC you sold me is broken or something...
Support: Well, what happens when you try to install it?
User: Nothing... actually, the cd thingy sounds a bit weird...
Support: Well, let's see, maybe the CD drive has a bit of dust or maybe...
(The technician opens the cd drive)
Support: ...
User: What?
Support: There are two cds in this drive
User: well, DUH!
Support: Excuse me, but why is the Office cd on top of the windows cd?
User: Well, the office cd says "It runs on windows 98", so...

Yes, this actually a true story... As true as another one of a user thinking that the mouse was used on top of the monitor, and another one where the user tried to use the mouse with his foot...[/QUOTE]


well I must say that def. was the good laugh I needed today LOL..woah amazing to think someone actually thought that was course of action to take....oh- my-goodness ;-))

thx for sharing...;-))

cheers
nl

---

### Post by AndersAA on 2005-06-17
[QUOTE=neighborlee]forcing someone ( with no option I mean ) to do archaic things like right clicking a desktop icon and going eject is at least IMO unnecessarily causing complexity to something that doesn't need to be for home users...so are you saying that all the other distros that do this are somehow going against the grain of wisdom in the linux world ?
[/QUOTE]

I'm not saying this solution is the best, I'm just saying it has it's advantages.  Forcing people to do things right isn't such a bad idea.  Oh, and windows has this for connected devices aswell you know.  "Disconnect removable device" thing in system tray when nothing is connected, it's just that nobody uses it, because it's so simpe to just pull things out like they do with cd's (that are read only anyway).  I've seen drives with filesystem errors many times because of this behavior.

[QUOTE=neighborlee]I must use windows and linux both and I can't tell you how much less hastle is involved when I just click eject button , and besides..since when is user friendly more appropriate when it takes twice as much input from a user to perform a specific function ? ;-)[/QUOTE]

If you can take the time to close any programs accessing the cdrom I dont see how right clicking and selecting eject is any more work.  It's more for you now maybe, because you're used to just clicking the cdrom, but I doubt you'll find it too troublesome if you get used to it.

---

### Post by neighborlee on 2005-06-17
[QUOTE=AndersAA]I'm not saying this solution is the best, I'm just saying it has it's advantages.  Forcing people to do things right isn't such a bad idea.  Oh, and windows has this for connected devices aswell you know.  "Disconnect removable device" thing in system tray when nothing is connected, it's just that nobody uses it, because it's so simpe to just pull things out like they do with cd's (that are read only anyway).  I've seen drives with filesystem errors many times because of this behavior.



If you can take the time to close any programs accessing the cdrom I dont see how right clicking and selecting eject is any more work.  It's more for you now maybe, because you're used to just clicking the cdrom, but I doubt you'll find it too troublesome if you get used to it.[/QUOTE]

okay few questions:

1) do you speak for ubuntu dev team and if so is this likely to remain as is eject wize ? ( lack of support for ejecting via button) [ since to my knowledge no dev member has ever commented on this topic]

2) how can I alter my system so eject does work via button ? ( assuming I dont first just get used to right click or  adding panel applet <G> )

thx
nl

---

### Post by AndersAA on 2005-06-17
[QUOTE=neighborlee]okay few questions:

1) do you speak for ubuntu dev team and if so is this likely to remain as is eject wize ? ( lack of support for ejecting via button) [ since to my knowledge no dev member has ever commented on this topic]

2) how can I alter my system so eject does work via button ? ( assuming I dont first just get used to right click or  adding panel applet <G> )

thx
nl[/QUOTE]

1 : no, I'm not a ubuntu developer.
2 : I have no idea, I've never wanted to do it so I've never explored the subject.  I believe supermount was the way of getting it to work, but that's now deprecated?

---

