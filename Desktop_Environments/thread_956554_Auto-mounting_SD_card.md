---
title: "Auto-mounting SD card"
date: 2008-10-23
forum: Desktop Environments
---

### Post by rawlyn on 2008-10-23
I've been trying to find a way to get the SD card slot on my Eee PC to auto-mount (running Ubuntu Eee with Gnome desktop). When I insert a card, it complains that I must be root to mount a drive.

After a lot of searching, I read about a package called ivman. I installed it and it works well except for a couple of little glitches:

[LIST]
[*] I still get the error about not being root. Any idea how I can stop this? I guess there's another service/app trying to mount it - can it be disabled? Is it a good idea to do that?
[*] Every time the device mounts, it seems to make a new directory in /media/ to mount the device to... :confused: How can I configure ivman to use the same mount point every time a card is inserted? (Something sensible like /media/sdcard would be nice).
[/LIST]

I've Googled this until I'm blue in the face... if I have found the answer, then I guess I didn't understand it... :(

Thanks in advance for any help with this one! Some things with Linux I'm really at home with, and other times it makes me feel like a total n00b!

---

### Post by jschramm97 on 2008-10-23
first i'm not going to take credit for this, i bought an Eee yesterday and wiped it before i ever started up the pre-installed xandros. anyways you have to rem out a statement in the fstab file. heres the instructions:

# Remove the cdrom line in fstab. The Ubuntu installer mistakenly adds the drive it was installed from to your fstab file as a CDROM. This means that SD cards (and USB drives?) will not be mounted properly.

Open your fstab file:
sudo gedit /etc/fstab

Find and comment out (by adding a # to the beginning of the line) the line referencing /media/cdrom. Reboot, and you should now be able to use SD cards again. 

----
this is a know issue with ubuntu, but i hope this helps. now off to fix my other issues. -Jim

---

### Post by sethvath on 2008-10-23
What is the /media directory it tries to mount itself to? some random number with hd722622?

One way to circumvent the issue with running as root on ivman is giving "yourusername" access rights to the /media/sdcard folder. Add yourusername to the same group and give it read+write access.

---

### Post by rawlyn on 2008-10-23
First of all, thank you both for taking the time to help me out.

I had already commented out the lines that referred to the cdrom drive in /etc/fstab - without doing that ivman didn't work at all. So I'm afraid that isn't the entire answer :(

In the initial situation, when I inserted the card it complained that I need root access to mount a drive. Then I found out about ivman, installed it, commented out the lines in /etc/fstab and tried inserting it again.

This time it mounted it to /media/usbdrive, and still came up with the original error dialog. It wouldn't let me unmount the drive for some reason, so as an experiment I took it out and inserted it again. It mounted to /media/sdc1 (along with error dialog). Repeat the process (bearing in mind I can't find a way to unmount it) and it mounts as /media/sdd1 (plus my friend the error dialog).

I'm thinking that maybe I don't need ivman at all (after all, it should "just work" right?), but maybe need to give myself permission to mount/unmount (as Ubuntu and/or Gnome seem to be _trying_ to mount it without ivman). Can someone explain further how I would go about doing that?

Thanks in advance!

---

### Post by rawlyn on 2008-10-23
Okay, time for an update...
I've given myself permission on /media with

sudo chown -R myusername:root /media

and left the entries in fstab commented (I guess they have nothing to do with this?). Now ivman is happy to mount the drive when I insert an SD card. However, it's mounting to /media/disk (which I admit is an improvement) and it's letting me unmount it by right-clicking the icon on the desktop.

All that's left is a niggling little detail really, but something I'd like to work out: I'd prefer it to mount to /media/sdcard. I've looked high and low trying to find where /media/disk is defined, but with no luck. Any clues anyone?

---

