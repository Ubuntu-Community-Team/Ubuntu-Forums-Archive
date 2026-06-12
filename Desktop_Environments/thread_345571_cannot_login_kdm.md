---
title: "cannot login kdm"
date: 2007-01-24
forum: Desktop Environments
---

### Post by syazli7 on 2007-01-24
I cannot login through kdm, after I enter my password and press Enter, the screen turns black like logging in, about 3 seconds the screen kicked back to kdm.
I'm able to login my username through tty1 (Ctrl+Alt+F1).
I'm able to login to my kde using root through recovery mode of grub and run startx.

The problem start with:

My kde hung for a couple of seconds, so I Ctrl+Alt+Backspace, but it didn't changed the screen, so I soft reboot, on loading the kubuntu blue splash bar, I heard one of my hard disk powered down and the screen hung, I soft reboot and I heard the same thing on loading grub and it hung, I hard reboot the same thing happened again, I thought it's hardware problem so I replug my molex power connecters.

I hard reboot and choose recovery mode from grub, I remember the screen tells me that I should run fsck, I had to umount my / partition, run reboot command and I don't hear the powered down sound anymore, the blue loading bar splash runs to the end and kdm starts, I'm not able to login through kdm.

I've done sudo dpkg-reconfigure kdm, no use.
I apt-get install kubuntu-desktop, no use.
I've install gdm in case only kdm not working, a screen saying there is some installation problem or that I may be out of diskspace when login through gdm.
I've created a new user through kde user management, I'm not able to login that user either through kdm/gdm.

Default desktop: KDE 3.5.5
I'm using IBM JFS filesystem for all my partitions except /boot which is ext3 on kubuntu edgy 2.6.17-10-generic

my df -h:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             2.0G  383M  1.7G  19% /
varrun                252M   12K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.0M  244M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              15M  9.4M  4.6M  68% /boot
/dev/hda6              36G   33G  3.2G  92% /home
/dev/hda7              36G   34G  1.3G  97% /shared
/dev/hdc1              36G   33G  2.8G  93% /storage
/dev/hda2             3.0G  2.0G  1.1G  65% /usr

---

