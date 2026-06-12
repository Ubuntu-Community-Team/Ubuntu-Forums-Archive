---
title: "Gnome doesnt show/automount devices (volumes, usbsticks, cd/dvd drives,...) anymore"
date: 2011-04-04
forum: Desktop Environments
---

### Post by kalzifer on 2011-04-04
Hello,

i'm using Ubuntu 10.04 since around juli 2010. Approximately one month ago i noticed, that the "Places" menu didn't show any volumes or discdrives anymore. But the devices are listed in /dev folder.
First i hoped this problem would disappear after an system update (at least this was true for another problem with my soundcard, which was resolved by a new kernelversion). In the meantime i googled a lot for this problem, but i didn't know what exactly to search for... i got a lot of talk about automounting (and the corresponding setting in gconf (i checked that, and the setting is set correctly)), or a problem at boot time when "/dev/null" can't be created and therefore udev isn't functioning correctly (sporadically i get the error when booting the system, but it doesn't seem to have any correlation to the problem described here). In conjunction with the /dev/null problem (i think) i rebuilt my initramfs (this was suggested somewhere in one of the google results, i'm really sorry, i can't remember where), but this didn't change anything regarding this problem.

So the question is, does anyone have a suggestion where to start looking for the reason of this problem?

Greetings and thanks in advance

---

### Post by Krytarik on 2011-04-04
Please post your "/etc/fstab", in code-tags please, the #-button in the editor.

Have a look at this guide:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Also, do you have access to your devices through "/media"?

---

### Post by kalzifer on 2011-04-04
Hi and thanks for your reply.

Here is the content of my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=528f349b-9b60-4f80-822b-670fea98d1cb /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=cc06888d-c88b-4c54-a8b8-558eacba2196 /home           ext3    defaults        0       2
# swap was on /dev/sdb8 during installation
UUID=38052474-456c-4141-adb0-ac68506ecf2e none            swap    sw              0       0


# Maxtor 300 GB

# /dev/sdb9 (jin)
UUID=c7638ea4-5b3d-486a-8df0-d1ab613aaf2e       /jin            ext3    defaults        0       2


# WD 1000 GB

# /dev/sda1 (kazuya)
UUID=2db65eb0-dc03-4084-bfc9-91d2d21a7d96       /kazuya         ext3    defaults        0       2


# WD 500 GB

# /dev/sde1 (heihachi)
UUID=6faf8ba5-c173-473c-95f2-2040077d9195       /heihachi       ext3    defaults        0       2

# WD 1500 GB

# /dev/sdd1
UUID=3b1c6519-7fdf-419b-9e8b-a37996f387c9       /hwoarang       ext3    defaults        0       2

```My /media folder is empty, to answer your second question.

---

### Post by Krytarik on 2011-04-04
That explains a lot! The "Places" menu only respects devices mounted to "/media". But regardless of that, you can access them at their respective mountpoints, right?

To make them appear in the "Places" menu, and all the other places, you could
a) mount them to "/media"
b) create directories in "/media" and "bind" them via "fstab" to the mountpoints
c) create symlinks in "/media" pointing to the mountpoints
d) try to find a way to convince "Places" to take your mountpoints into account, I don't know if that is possible

---

### Post by kalzifer on 2011-04-04
Before the problem started to occur my "/media" folder was populated automatically with all partitions of my hdds that were not mounted in fstab, my dvd writer and all connected mass storage devices (usb sticks, camera etc.). This is the expected functionality, is it?
This also means that an usb stick that i connect is not mounted automatically anymore, BUT i can see the corresponding device when i call for example "sudo fdisk -l".

To make that clear: the mountpoints in the fstab are not the problem, i have bookmarks for them in nautilus. It is all the other stuff that was detected automatically and put into the "/media" folder. For example: i have a harddisk only for windows partitions. They are not mounted when i boot ubuntu, but they were visible in the "Places" menu and when i click on "Computer" in the "Places" menu (under "Computer" only the entry "File System" is left), so i could simply click on them to mount them, if needed.

---

### Post by Krytarik on 2011-04-04
> **kalzifer said:**
> This is the expected functionality, is it?

Yeah, that's right! Did you do anything to "fix" this behaviour?

**EDIT:** I believe, the only solution for this is to add the partitions of your 'Windows' disk to "fstab" as well, and set the "noauto" option for them.

---

### Post by kalzifer on 2011-04-05
I can't remember "fixing" something, but i can't exclude the possibility, that i changed something unknowingly while trying to fix another problem...

The suggested solution to add entries to the fstab is not satisfying in my opinion. I know definately that all worked fine about a month ago, with the same fstab. Before doing such a workaround, i would reinstall the whole system.

But I searched for clues another 2 hours, and found an interesting issue:

When i open the gnome-disk-utility from the System-menu no devices are listed. So I started it from the console, and this is the output i gave me:

```

(palimpsest:4790): libgdu-WARNING **: Couldn't get daemon properties
Error creating pool: `(unspecified error)'

(palimpsest:4790): Palimpsest-CRITICAL **: Bailing out

```

So I wondered what daemon properties could be meant, and google around a bit. I found that there is a startup application "Disk Notifications" related to the Disk Utility (/usr/lib/gnome-disk-utility/gdu-notification-daemon). I checked if it was running on my system, and it was not. Then i tried to start it in the console and it gave following output:

```

(gdu-notification-daemon:4803): libgdu-WARNING **: Couldn't get daemon properties
======================================================================
Error constructing GduPool: (unspecified error)

This error suggests there's a problem with your udisks or D-Bus installation.
======================================================================

(gdu-notification-daemon:4803): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:4803): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:4803): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:4803): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:4803): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:4803): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:4803): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:4803): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
**
libgdu:ERROR:gdu-pool.c:2459:gdu_pool_get_devices: assertion failed: (pool != NULL)
Aborted

```

The important information being "This error suggests there's a problem with your udisks or D-Bus installation.".

So i checked out information about DBus and UDisks... Seems that DBus is deprecated, but still present in Ubuntu 10.04. The DBus daemon is running in my system, but no sign of any UDisks daemon. But I checked Synaptic, and udisks is installed (although i dont know if this includes the daemon or only the console client).

So i tried the udisks console client and called "udisks --dump". This is the output:

```

(udisks:4806): udisks-WARNING **: Couldn't enumerate devices: Cannot launch daemon, file not found or permissions invalid

```

I also called it as root to exclude any permission issues... same result.

How can i make sure that dbus and/or udisks are correctly installed/configured?

---

### Post by kalzifer on 2011-04-05
Problem solved.

After suspecting a problem with the udisks-daemon i reinstalled it, and all is fine again. All drives/volumes are diplayed under "Places/Computer" again.
The "Places" Menu itself wasn't updated, but a restart of the system fixed that too.
Automounting of USB Drives also works again and the Disk Utility shows all disks :)

---

### Post by Krytarik on 2011-04-05
Good to know! I remembered encountering a similar issue before, but I didn't know anymore if the concerning devices were listed in "fstab" or exactly how it was. The next time I encounter such an issue, I know at what a have to look.

---

### Post by elvis_ef on 2012-03-07
Hi, I have a similar problem, but the reinstallation of udisks didn't help. Any ideas for a solution to that problem ?

When I want to start palimpsest, it shows me nothing.. no disks, no info... In the terminal I have this info:
> (palimpsest:4975): libgdu-WARNING **: Couldn't get daemon properties
Error creating pool: `(unspecified error)'

(palimpsest:4975): Palimpsest-CRITICAL **: Bailing outWhen I enter "udisks --dump", it shows me:
> (udisks:4984): udisks-WARNING **: Couldn't enumerate devices:  Cannot launch daemon, file not found or permissions invalidI  tried reinstalling Dbus and Udisks - nothing happened, no changes. Maybe  some services need to be run? Udev etc..? But they're still there, in  memory. When I plug in a new usb hdd, it's being detected in the system  but still doesn't show in Nautilus.

One more info, when I try to run "/usr/lib/gvfs/gvfs-gdu-volume-monitor", terminal shows me:

> (process:5198): libgdu-WARNING **: Couldn't get daemon properties
======================================================================
Error constructing GduPool: (unspecified error)

This error suggests there's a problem with your udisks or D-Bus installation.
======================================================================

(process:5198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:5198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(process:5198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:5198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(process:5198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:5198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(process:5198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:5198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
**
libgdu:ERROR:gdu-pool.c:2565:gdu_pool_get_presentables: assertion failed: (pool != NULL)
AbortedGenerally my system software is a one big meta-package, so If I want to  remove for example udisks, in order to install it again,  can't do that.  I can only use reinstall option.

anyway... I'm stuck.. maybe some suggestions.. ?

My system is: Ubuntu 11.10 (on-line upgrade from 11.04)

thanks in advance..

---

### Post by Murz on 2012-11-22
Got the same problem on Ubuntu 12.04 when running as user:
```
$ udisks --dump

(udisks:8121): udisks-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

But if I run this as root, all works good. Reinstalling isn't help.

elvis_ef, did you find any solution for this problem? Is this command work from root user on you compute?

---

### Post by wildmanne39 on 2012-11-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

