---
title: "prevent single Automount-Symbols on XFCE Desktop"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-11-03
Hey there..!


I've looked over to the most promising thread concerning this matter:

[http://ubuntuforums.org/showthread.php?t=223400](http://ubuntuforums.org/showthread.php?t=223400)

but the method via 'gconf-editor' works only on gnome, and the mounting in /mnt instead of /media will not prevent the symbols from showing on the desktop.

Don't get me wrong: I DO want the drives to be auto-mounted, but not all to be symlinked to the Desktop (most especially FD).


perixx

---

### Post by bapoumba on 2007-11-03
> Settings > Desktop > Behavior > Untick removable devices

---

### Post by perixx on 2007-11-04
> > Settings > Desktop > Behavior > Untick removable devices

!=

> prevent **single** Automount-Symbols on XFCE Desktop

&

> Don't get me wrong: I DO want the drives to be auto-mounted, but **not all** to be symlinked to the Desktop (most **especially FD**).


;]

but thanks for your reply.


perixx

---

### Post by bapoumba on 2007-11-04
Eheh, sorry :)

What I do, then, is to mount the drives in /mnt/<whatever> (just choose a mount point). Anything mounted in /media will show up on the desktop. Therefore, anything mounted elsewhere won't.
You need to make the mount point and edit the fstab.

BTW, what is FD? (floppy disk?)

---

### Post by perixx on 2007-11-04
> and the mounting in /mnt instead of /media will not prevent the symbols from showing on the desktop.


==

> mount the drives in /mnt/<whatever> (just choose a mount point). Anything mounted in /media will show up on the desktop. 

^^

erm... you did READ my post in the first place, did you?
:]


perixx

---

### Post by bapoumba on 2007-11-04
Woops, yes I did, yesterday.. Sorry again.

I really do not see why drives mounted in /mnt show up on the desktop. Did you edit the /etc/fstab file? Could you please post it in here?
```
cat /etc/fstab
```
Editing the fstab takes effect at next login in the session (no need to reboot).

---

### Post by perixx on 2007-11-04
here goes:

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=120247a9-3e01-440c-b2cf-cb70e9321988 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=e37de1b8-9e7f-4e53-b8d7-40cd5bbe8da7 none            swap    sw              0       0
/dev/hda6 /home ext3 nodev,nosuid 0 2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



KEEP IN MIND, THOUGH (^^)

that I've changed this back from /mnt to original /media, when it didn't work out for me!

> /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I'd be really grateful if you have some idea in store about this in spite :)

perixx

---

### Post by bapoumba on 2007-11-04
Okay, this is part of my fstab:
```
# /dev/hda2
UUID=0A2A-1AD4  /mnt/ACER     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=c3868c20-c310-476c-b73d-e39888aac798 /mnt/Storage     ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Works fine with the two partitions on the hard drive.

I changed the mount point for my cdrom:
```
/dev/hdc        /mnt/cdrom0   udf,iso9660 user,noauto     0       0

```

And indeed it shows up on the desktop, even if mounted in /mnt/cdrom0
I guess cdroms, floppies and may be other devices obey different rules (I mount my palm in /mnt, and it works okay).
I'll check.

---

### Post by perixx on 2007-11-04
Thank you for investigating!

---

### Post by perixx on 2007-11-04
2 quick questions off-topic, if you don't mind:

- Is it generally save to do
> sudo apt-get autoremove 
to remove orphaned packages, or could I spoil installations from Synaptic with that command?

- can I savely add the 'recommended feisty-updates' beneath the 'security feisty-updates' in the Repository-Manager? Or am I in danger of automatically upgrading to Gutsy / spoiling existing programs with this feature?

Oh, and, I got three other urgent problems - perhaps you could also have a quick look at them, please ??

```
http://ubuntuforums.org/showthread.php?t=602409

http://ubuntuforums.org/showthread.php?t=601847

http://ubuntuforums.org/showthread.php?t=600519

```
 

perixx

---

### Post by bapoumba on 2007-11-04
For the autoremove, I think so, yes, but I never used it myself (I use aptitude). In any case, you'll have to accept the actions, so if autoremove wants to remove a whole bunch of packages and you do not feel some of them must go, you can cancel.

For the automounts of removable devices, I did not find anything that you can use drive by drive. And the cdrom, floppies etc are indeed always showing up on the desktop. Looking at bugs where they were not any longer, it always was a hal, udev or mount issue, things you would not want to mess around with.

Has anyone an idea about this?

---

### Post by perixx on 2007-11-04
ah, too bad... I thought it was only some 'config-file' to edit away, in order to edit single mounts :/ 
could it be that such a file can be found somewhere in gdb or xfce folders?

well, I tried autoremove and it did show me a whole bunch of packages to remove (including openoffice, which made me nervous) and I decided to stop the process.


perixx

---

### Post by perixx on 2007-11-04
*bumpsInHopeSomeOneHasStillAnaIdea*

---

### Post by perixx on 2007-11-07
*bumpgiveitanothertry*

---

### Post by tjrm on 2008-01-06
Found this reference for adjusting which icons show on dektop:

[http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README]("http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README")

---

### Post by perixx on 2008-01-07
thx tjrm, 
but those settings you can already set in the desktop-settings GUI of Xfce. What I was looking for, is some possibility to keep certain single drives (e.g. when they're treated as removable) from showing up on the desktop. Currently, enabling 'removable' will resulte in showing everything that's been found.

perixx

---

### Post by bapoumba on 2008-01-07
@ yy17616433: :confused:

---

### Post by perixx on 2008-01-07
I suppose you're referring to this one:> result[COLOR="Red"]e[/COLOR]
You're always welcome to correct things, if you got time to help improving other ppls. orthography, Mr. 'yy17316432' ^^

Hello bapoumba :) long time no see *g*

perixx

---

### Post by bapoumba on 2008-01-07
Hello perixx. I sadly see your issue is not solved :(

---

### Post by perixx on 2008-01-07
Nah, it isn't :-| But it's a small issue anyway ;-]

perixx

---

