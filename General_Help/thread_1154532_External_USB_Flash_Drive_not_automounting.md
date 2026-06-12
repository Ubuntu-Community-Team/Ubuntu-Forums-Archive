---
title: "External USB Flash Drive not automounting"
date: 2009-05-09
forum: General Help
---

### Post by mark2741 on 2009-05-09
I have a SeaGate FreeAgent Pro external USB hard drive that I use as a data/music storage drive.

For some reason, Jaunty will not automount it unless, after I boot up, I unplug and replug in the USB drive into the USB port. In other words, it doesn't automount the drive when Ubuntu boots up.

I'm using 9.04, gnome, and 64-bit version.

What can I do to fix this? The USB drive is in another room (the USB cable goes through a wall jack, to the computer on the other side). It's only about 5 feet away but I'd have to go into the other room every time I reboot Ubuntu to unplug/plugin the drive, and I'm too lazy for that! : )

---

### Post by hexanol on 2009-05-09
Well, add a line in /etc/fstab, preferably using a UUID to identify the block device. But I wonder what is the behaviour if a filesystem listed in fstab can't be found... you could otherwise write a bash script, I guess...

If you need more help, just ask. :)

---

### Post by mark2741 on 2009-05-09
I have no idea how to do any of the things you mentioned. Can you tell me how step-by-step?

---

### Post by hexanol on 2009-05-10
If you do add a line in /etc/fstab to mount your "drive" (actually the filesystem on your drive), the behavior will be somewhat different then when you just unplug and replug it. First, the drive won't be shown on your desktop (but nothing stops you from putting a link to the root of your drive on your desktop) and if you want to unmount it, you mostly will have to enter a command in the terminal.

You could also look at the "Disk Mounter" panel item. Right click on your top panel, click Add to panel... and look for "Disk Mounter". You then will be able to mount/unmount your drive from a simple click.

I guess there's other solutions, I just don't know them all (and yeah, I won't look for all anyway).

If you do want to go with adding a line in /etc/fstab... well, just ask. :P

---

### Post by mark2741 on 2009-05-10
I tried Disk Mounter and it recognizes all of my drives/partitions except for the external USB drive. The problem isn't in mounting/unmounting, it's that Ubuntu doesn't recognize it as being physically connected at all on boot.

---

### Post by hexanol on 2009-05-10
Hum, that's weird. Must say, I didn't upgrade to 9.04 (and from the number of problems I saw, I doubt I will do it soon).

So, if you start your computer and enter a command like "sudo fdisk -l", it will not show your external drive, is it right ? If it is, then adding a line in /etc/fstab won't resolve your problem, and I won't be able to help you more.

---

