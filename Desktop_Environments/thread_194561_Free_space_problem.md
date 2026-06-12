---
title: "Free space problem"
date: 2006-06-11
forum: Desktop Environments
---

### Post by ajgreeny on 2006-06-11
I have a slight problem which I probably brought on myself but I'm sure there must be a way to overcome it.

I have two hard disks, hda and hdb.
Hda has winxp (hda1)and dapper drake (hda2) on it, hdb just has dapper drake which I use as a test bed to try all sorts of silly things that may break the system.  It doesn't matter if that is what happens because I have my main system on hda2.
I installed hdb with dapper first to see if all went OK, copying across all my own files from the previous breezy install on hda2.
When I saw how great dapper was I installed onto hda2 as well in place of breezy.  I then copied across all my own files from home of hdb but stupidly did it when booted into dapper on hdb.  This meant all the permissions were wrong in hda2 and I had to delete them all and copy across again while booted into hda2 this time.  Great, they all work OK.

BUT-----

If I use *df -h* to show disk usage, or use *gparted* or *gnome system monitor* they all show a huge amount of space used (35GB), which does not show up in konqueror, where properties of the file system show the right amount used.  The drive icon on the desktop shows correct usage of:-

19.1 GB
20,524,508,326
127223 files
14321 subfolders

All this extra space usage appears to be from the trashed home files which I copied across incorrectly and are now in /root/.local/share/Trash/files/files and which I am reluctant to delete as I'm afraid I may break the system.  There are about 16GB, however, which I want to free up.  Can I do this in a root session in konsole safely or if not how should I proceed?  Would it be beter to do it in recovery mode, ie the second item on my grub menu which I think gives me root access.  Help please,  16GB is a lot of disk space to lose to rubbish.

---

### Post by ajgreeny on 2006-06-11
OK you can all forget it now.  I,m amazed how you can so easily overlook simple things like the wastebin icon when I start konqueror with *kdesu konqueror*.  That got rid of everything cleanly after putting all that was in the /root/.local/share/Trash/files/files folder into the wastebin from the konqueror started as root.
Now I have all my space back and all is working beautifully.  I even forced a fsck on restart to make sure everything was alright.

Isn't linux brilliant?  In windows by now I'd be pulling my hair out and probably getting ready to reinstall.  Sorry for wasting space on the forum (as well as my hard disk)

---

### Post by msandersen on 2006-06-12
[QUOTE=ajgreeny]Isn't linux brilliant?  In windows by now I'd be pulling my hair out and probably getting ready to reinstall.[/QUOTE]
Except of course in Windows you wouldn't *have* this problem, nor need to use the commandline :) Permissions? What permissions? Which is a large part of its troubles, I suppose. But Linux still have a long way to go to match XP userfriendliness, alas :(

---

### Post by aysiu on 2006-06-12
[QUOTE=msandersen]Except of course in Windows you wouldn't *have* this problem, nor need to use the commandline :) Permissions? What permissions? Which is a large part of its troubles, I suppose. But Linux still have a long way to go to match XP userfriendliness, alas :([/QUOTE] A long way to go? All it needs is a "browse as root" button, which Knoppix and Mepis have, incidentally.

And it's not that hard to create on in Ubuntu. Right-click. Type ```
kdesu konqueror
``` Close.

---

### Post by ajgreeny on 2006-06-13
[QUOTE=aysiu]A long way to go? All it needs is a "browse as root" button, which Knoppix and Mepis have, incidentally.

And it's not that hard to create on in Ubuntu. Right-click. Type ```
kdesu konqueror
``` Close.[/QUOTE]

Yes, aysiu, I already have this root file manager link on my desktop and use it occasionally, not too much.  My first problem, however was simply finding where the many GB of space had gone, because I just simply couldn't find it.  Now that I have, and have gone through this whole problem and solved it, I feel I know a great deal more about the workings of linux in general, and (K)ubuntu in particular.

Thanks for your comments, everyone.

---

### Post by msandersen on 2006-06-13
[QUOTE=aysiu]A long way to go? All it needs is a "browse as root" button, which Knoppix and Mepis have, incidentally.

And it's not that hard to create on in Ubuntu. Right-click. Type ```
kdesu konqueror
``` Close.[/QUOTE]
I got something similar from Automatix. Either from the Applications menu or from right-clicking the Desktop, under Scripts are gedit as Root and Nautilus as Root. Don't know where those menu items are stored, but I assume it's simply "gksudo gedit" or the like. Very handy to have. I prefer Gnome, though it's not as advanced as KDE/QT in various ways. When I can afford a bigger hard drive, I'll make more space for Ubuntu and try out Kubuntu-desktop (this old test machine has only a 10Gb HD, with 5 for Ubuntu, 3 for the system).
OT: Speaking of Mepis, I had it on here previously. I still have a Mepis 3.4.3 live CD which is handy when I've had problems with Ubuntu, since frankly it's better than the Ubuntu Live CD, especially for this machine due to the Integrated Graphics. Ubuntu, like XP actually, switches to the Integrated Graphics at the login rather than the graphics card by default. You can't easily fix that on a live CD. Mepis handles it without trouble. They have a Mount applet on the menu which is also handy. KDE seems faster than Gnome, though not as fast as XP (which on this hardware is not very), but it is too Windowsy and cluttered for my liking.

---

