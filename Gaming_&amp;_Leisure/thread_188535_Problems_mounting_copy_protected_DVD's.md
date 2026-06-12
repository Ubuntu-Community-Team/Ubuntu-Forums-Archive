---
title: "Problems mounting copy protected DVD's"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by Grue on 2006-06-04
Sorry for the double post, but I just remembered this subforum and thought it probably was more fitting here...

I've just installed Ubuntu 6.06 on my brothers computer, since he was in awe after watching my install. Problem is, Ubuntu won't mount his Civ4 CD because of missing permissions. Cedega complains about this also in it's setup, but the fix provided doesn't work (chmodding hda with 644).

The computer automounts 'normal' DVDs/CDs without problems, but when I try to access the Civ4 CD it gives the error:
 "The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "cdrom"."

The Cedega error is:
```

A problem was detected with your CD/DVD-ROM devices.  Some or all copy protected games
may not work correctly with your drives.  Check the permissions on your CD/DVD-ROM device (in /dev). The device can be found in the /etc/fstab file.

In a terminal perform:

ls -la /dev/CDROM (where CDROM is the device for your system)

Make sure that all users have rx permissions.  If users do not have rx permissions then add the permissions by running

The device may be a symbolic link to a second device, for example:

lrwxrwxrwx  1 root root 3 Mar 23 05:50 /dev/cdrom -> hdc 

Here we can see that /dev/cdrom is a link to /dev/hdc.  Be sure to check permissions on the symbolically linked devices as well.

```

I'm really miffed about this, since he won't use Ubuntu/Linux if I can't get this up and running before tomorrow evening when he goes home...

I don't understand why fdisk -l doesn't list the two DVD drives, even when a CD is mounted, but maybe this is because it's handled by udev in a special way?

---

