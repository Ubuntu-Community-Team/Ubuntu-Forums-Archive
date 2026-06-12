---
title: "Meerkat won't mount floppy"
date: 2011-04-05
forum: Desktop Environments
---

### Post by Jeff Root on 2011-04-05
In Karmic Koala I can mount a floppy disk with a launcher I made
and put in the Applications menu.  I set the Type to Application
in Terminal.  The command is: mount /media/floppy
 
It doesn't work in Maverick Meerkat.  The floppy drive clunks and
runs when I click the launcher, but the files are not read and the
disk isn't mounted.  Clicking on the Floppy Drive links that always
appear in Nautilus but never work (even in Koala) still don't work.
The drive clunks and spins, and I just get the message, "Unable to
mount location - No medium in the drive".
 
It might be a permissions problem, but I don't get any warning
message about permission.  If I changed some permission in Koala
I didn't make a record of it and have forgotten.  Worse, I can't
find the launcher in Meerkat's filesystem, or any info about the
launcher's permissions anywhere.
 
   -- Jeff, in Minneapolis

---

### Post by coffeecat on 2011-04-06
Difficulty in mounting floppies is a long-standing unresolved issue which is clearly not being taken seriously, unfortunately.

Try this command with a floppy in the drive:

```
udisks --mount /dev/fd0
```If that works, you can make a launcher with the command.

---

### Post by Jeff Root on 2011-04-07
Thank you!  That worked perfectly.
 
   -- Jeff, in Minneapolis

---

### Post by machdohvah on 2011-04-07
I am very interested in the answer to this also for most of my files are on floppy..

---

### Post by machdohvah on 2011-04-07
"Cannot stat device file /dev/fd0: No such file or directory"

---

### Post by coffeecat on 2011-04-07
> **machdohvah said:**
> "Cannot stat device file /dev/fd0: No such file or directory"

Have a look in /dev. Your floppy device may appear as fd1. Or if there is no fd* in /dev at all then your system is not detecting the floppy drive.

Or - you typed fd-zero in your post, but are you sure you did in the terminal? It's an easy mistake to make. If there is a fd0 in your /dev, then make sure you are typing fd-zero in the terminal and not fd-CapitalO.

---

### Post by kapetr on 2011-04-07
I had Problems with floppy in U10.10 too.
It is persistent problem with Ubuntu.

As I had Googled - it helps to remove/comment_out the floppy line in /etc/fstab.

Don't ask my why ... (?!?!?)

Before that - Ubuntu was crazy - the mount failed or sometimes not, but no files was accessable and no unmount possible, ... 

After that it is possible to mount floppy wit standard "mount" command.

I really CAN'T UNDERSTAND, why this Bug is still not solved!

---

### Post by machdohvah on 2011-04-07
OK, I looked at that file and I could not figure out what line I was suppose to comment out. There seems to be no reference to a floppy drive in "/etc/fstab". I use wine-1.2.2 with ubuntu 10.10 -  the Maverick Meerkat. I am having problems mounting the floppy USB drive. "Places -> Computer" sees an icon labelled "Floppy Drive", but it cannot see any files on the disk. "System -> Administration -> Disk Utility" sees "Floppy Drive" with "Connection: USB at 12mb/sec". The thing that is different is that the last screen mentioned also sees "Device: /dev/sdb" with "Capacity: No media detected". I am new at this and cannot figure out how capture a screen shot of the Drive Utility page. While back at "Paces -> Computer -> Floppy Drive -> Properties" there is a entry:"Location: Computer:///" which do not agree. What should I do?

Michael Flower in Las Vegas, NV
[email]machdohvah@gmail.com[/email]
Ubuntu 10.10 - the Maverick Meekat
dosemu-1.4.0.1
wine 1.3.17
floppy: Model: MITSUMI USB FDD 061M

---

### Post by kapetr on 2011-04-08
With USB floppies I do not have any  experience, sorry.

Far as I know GNOME (or KDE) listens for d-dus events like hot-plug (if you attach yours USB floppy) and takes "actions" - e.g. mounts the device and opens Nautilus.

See: [http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus) (../Udev, ../DeviceKit).

I don't know, if USB floppy makes something if floppy-disk is inserted. Normal floppy does not - so it is necessary to click on this "place". But as I wrote, in Ubuntu is problem with floppies :-(


BTW: The screenshots (current window or whole screen) are made with keyboard key "PrintScr" or "Alt+PrintScr"  (? I'm not sure, what is default)- see system->preferences->keyboard_shortcuts.

--kapetr

---

