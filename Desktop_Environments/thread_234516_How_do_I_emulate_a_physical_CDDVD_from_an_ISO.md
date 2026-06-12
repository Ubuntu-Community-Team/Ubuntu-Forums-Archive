---
title: "How do I emulate a physical CD/DVD from an ISO?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by htmlguy716 on 2006-08-11
There are certain proprietary programs I use (some games, for example) that require a CD/DVD to be inserted for the program to run. This is not only inconvenient, but rather ineffective as an anti-piracy measure &#8211; anyone could just copy the CD if they wanted to. I was wondering if someone knows a way to trick Linux into thinking an ISO is a mounted CD (kind of like Alcohol 120% on Windows), so I don't have to manually insert the correct CD each time I use a program. If this is impossible, I'll just stick with the manual method.

---

### Post by pheex.net on 2006-08-11
The command your looking for is:

sudo mount -o loop /path/to/iso /path/to/mountpoint

For more information read the man page for mount and you will find an entire section about "THE LOOP DEVICE"

Good luck

---

### Post by stinerman on 2006-08-11
Its actually quite a bit easier in GNU/Linux systems to mount an ISO file:

mount -o loop -t iso9660 <filename> <mount point>

---

### Post by rykel on 2006-08-11
> **stinerman said:**
> Its actually quite a bit easier in GNU/Linux systems to mount an ISO file:

mount -o loop -t iso9660 <filename> <mount point>

Hi,

I wonder if there is any GUI to do it?

In fact, is there any GUI program in Linux that works like Daemon Tools for Windows?

---

### Post by stinerman on 2006-08-11
Apparently there is a program, [CDemu]("http://cdemu.sourceforge.net/").

It isn't in the repos, so you'll have to download and compile the source, or perhaps google for a .deb package.

---

### Post by christhemonkey on 2006-08-11
You can use a nautilus script:
```
sudo apt-get install nautilus-script-manager 
```
Then save the script from here:
[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/](http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/)

into your ~/.gnome/nautilus-scripts

---

### Post by rykel on 2006-08-11
> **stinerman said:**
> Apparently there is a program, [CDemu]("http://cdemu.sourceforge.net/").

It isn't in the repos, so you'll have to download and compile the source, or perhaps google for a .deb package.

I am googling now for a deb... but it would be great if cdemu is available as an autopackage. ([http://www.autopackage.org](http://www.autopackage.org))

I love autopackages because I can install them as User, not just root.

---

### Post by htmlguy716 on 2006-08-13
Thank you very much for all the help. Doing this: ```
sudo mount -t iso9660 -o loop myiso.iso /mnt/cdrom0
``` seems to accomplish what I wanted.

---

