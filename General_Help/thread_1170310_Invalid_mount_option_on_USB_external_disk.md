---
title: "Invalid mount option on USB external disk"
date: 2009-05-26
forum: General Help
---

### Post by pwab on 2009-05-26
Hi,

I installed ubuntu about a month ago and I've been using my external harddrives all through this time. Then, last week, I installed kubuntu-desktop via synaptic, and since then I get this error when I insert my external USB harddrive.

[INDENT]Cannot mount volume:
Invalid mount option when attempting to mount the volume "New Volume"[/INDENT]

I've seen similar errors on the net, but no fixes. Does the kubuntu installation have anything to do with this error? 

Please see the screenshot with the error and syslog output. my fstab follows:
[INDENT]proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=55465143-dd89-4c79-932a-8257aa8f4e4a /               ext4    relatime,errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=49DF587C6200381A /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=00984b88-9e67-4f18-ac1d-fb5c9a9948f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/INDENT]

[img]http://www.imagechicken.com/uploads/1243331914009012500.png[/img]

---

### Post by livestockPimp on 2009-05-26
first of all have you tried mounting it by the command prompt?

to do this open a terminal, and type:

"sudo mount /dev/sda1 /mnt"

replacing "/dev/sda1" and "/mnt" with the device and mount point.

---

### Post by pwab on 2009-05-26
Thanks for the quick reply. Yes I just did that, here's the output:

[INDENT]pieter@jeapieta-pc:/media$ sudo mount /dev/sdb1 /media/disk
pieter@jeapieta-pc:/media$ cd disk
pieter@jeapieta-pc:/media/disk$ ls[/INDENT]

with output that's correct. I browsed the disk via gnomes file manager, etc, all works correctly.

[INDENT]pieter@jeapieta-pc:/media$ sudo umount disk[/INDENT]

works, does what is expect. then: unplug, plug in again, get the same automounter error.

---

### Post by livestockPimp on 2009-05-26
ok,
well next questions, can you mount other USB drives from your PC with automounting?

also, fstab is used for when the system is booting and what to mount then and not automount.

have you had a look at this? appears to be a similar problem?

---

### Post by livestockPimp on 2009-05-26
[https://bugs.launchpad.net/ubuntu/+bug/210613](https://bugs.launchpad.net/ubuntu/+bug/210613)

---

### Post by pwab on 2009-05-26
It looks like it could be a similar problem than the one in bug 210613, but I don't quite know how to implement the fix. I opened gconf-editor as myself and as a sudo command, edited the defaults and my settings. I removed everything I could see, but I still get that error.

What are the default mount options for those settings? Some time ago I changed those default settings for ntfs-3g to include gid=users so that both me and my wife could have access to the files on the external disks, regardless of who mounted the volume. I've removed this extra option, but as I said, I still get exactly the same error. The little unmount tool in the notification area has a grayed out option with the plugged in drive, but I can't actually mount it. I see it in the file manager, but if I click on it, it fails...

oh, and I can't mount other drives anymore either :(

---

### Post by pwab on 2009-05-27
one new thing. if i log in to a kde session and plug in the device, it works fine... is it possible for there to be some kind of conflict between the kde and gnome device mounters?

---

### Post by pwab on 2009-05-29
Thanks for all the GREAT tips. I solved the problem like this:

Remove kubuntu like here ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome))
in synaptic, search under installed packages for everything that matches 'mount', mark them all for reinstallation... reboot... twice...

---

