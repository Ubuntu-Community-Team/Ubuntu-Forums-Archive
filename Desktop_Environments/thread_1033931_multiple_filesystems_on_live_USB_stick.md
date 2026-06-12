---
title: "multiple filesystems on live USB stick"
date: 2009-01-07
forum: Desktop Environments
---

### Post by davidshere on 2009-01-07
I followed the directions here [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680") to create a live usb stick, and when I boot up, I have quite a few mounted filesystems, some appearing to be duplicates of each other. 

```
david@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M     0  362M   0% /lib/init/rw
varrun                362M  116K  362M   1% /var/run
varlock               362M     0  362M   0% /var/lock
udev                  362M  2.8M  359M   1% /dev
tmpfs                 362M  252K  362M   1% /dev/shm
rootfs                2.0G  563M  1.3G  30% /
/dev/sdb1             3.9G  2.7G  1.2G  70% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 2.0G  563M  1.3G  30% /tmp
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
gvfs-fuse-daemon      2.0G  563M  1.3G  30% /home/david/.gvfs
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/fuse             2.0G  563M  1.3G  30% /home/david/.gvfs
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM
tmpfs                 362M  2.0M  360M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              11M   11M     0 100% /media/CDROM

```

I've been having a problem where the system will run for a while, and then become unstable (unable to save changes to files, unable to launch new applications), and the only solution is a hard reboot.  I'm wondering if these multiple filesystems are the cause of this.

The USB "System" in question is a 4GB Sandisk Cruzer Micro running 8.10 desktop.  I've been using this system daily for about two weeks.  I've only had one other problem -- it won't remember my time zone.  Other than that it's been fairly smooth.

---

### Post by krisrowland on 2009-04-17
Hi David.

About that multiple filesystems thing... I have no idea, and it's really bugging me. I, too, would like to know what the *tempfs* entries relate too and whether it's an artefact of the Casper architecture the persistent Live Ubuntu installs use. Also, I've noticed that more and more *tempfs* entries get added on each successive boot (I boot to it from 2 different computers per day, on average). Since each is listed as at least 2MB, I'm concerned that it's going to start taking up unecessary space. Again, no idea... My best guess is that they represent different snapshots of system changes as caught by the Casper architecture. Can anyone help here?

Regarding the time-zone not being remembered, I had exactly the same issue with my persistent Live USB Ubuntu 8.10 install. I managed to correct it only by manually resetting the *tzdata* to my time-zone. The command now runs automatically at startup. I've discussed it on [my bLog]("http://krisrowland.wordpress.com/") [here]("http://krisrowland.wordpress.com/2009/04/09/fixed-gnome-clock-shows-wrong-time-gmt-utc-instead-of-local-in-persistent-live-usb-ubuntu-810/"). I've had a lot of other issues that I've fixed which you can read about from [this post]("http://krisrowland.wordpress.com/2009/04/02/persistent-resizable-live-ubuntu-810-install-on-a-usb-drive/") (the links at the bottom of the page to my other posts might be of most interest for you).

Thanks,
Kris

---

### Post by davidshere on 2009-04-17
I had one other problem: The system would lock up frequently.  After a while, no programs would launch, and some running programs would stop responding. 

I fixed this and the other problems above by installing Ubuntu to the flash drive instead of using it as a live CD with persistence:

[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372)

... and my life is much happier now.

---

### Post by krisrowland on 2009-04-17
> **davidshere said:**
> I fixed this and the other problems above by installing Ubuntu to the flash drive instead of using it as a live CD with persistence ... and my life is much happier now.

Excellent. I may just do the same thing once Jaunty is out. I'll stick with my currently still functioning live install until then, I suppose.

I'd have tried that technique first but I have a friend who says that GRUB has issues with booting from his USB device and that often his USB partitions would be labelled differently when used on different computers. I think I'll put that down to him using it on an old laptop, though. Sounds like everyone using a direct install to USB has had few issues.

Thanks :)

---

### Post by davidshere on 2009-04-18
Actually I did this because I inherited an old laptop that had an unusable hard drive.  the USB Ubuntu drive is my only drive.

---

