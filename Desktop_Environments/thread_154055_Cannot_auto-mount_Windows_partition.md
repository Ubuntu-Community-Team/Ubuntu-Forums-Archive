---
title: "Cannot auto-mount Windows partition"
date: 2006-04-02
forum: Desktop Environments
---

### Post by Etoile on 2006-04-02
For some reason, edits I make to /etc/fstab don't work.  When I boot I get the "Mounting local filesystems.........[color=red]failed[/color]" error, and indeed my partition is not mounted.  I've looked at a bunch of threads about this but I'm not finding anything that seems to answer why I can't effect changes in /etc/fstab.  (I'm editing it with sudo of course.)

My /etc/fstab is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc2       /mount/windows  ntfs    nls=utf8,umask=0222 0       0

```
I'm still trying to figure out how to run things automatically at startup, too - like an equivalent of the Startup folder in Windows.  Is there a way I can just run this at startup?  It works just fine, but I'm concerned about being able to put in the password (for sudo) using a .sh script.```
sudo mount /dev/hdc2 /mount/windows -t ntfs -o nls=utf8,umask=0222
```

---

### Post by jetix on 2006-04-08
take that [http://ubuntuguide.org/#automountntfs]("http://ubuntuguide.org/#automountntfs")

---

### Post by aysiu on 2006-04-08
Or

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

**Edit**: Took a second look at your /etc/fstab file, and it looks good. Do you actually have a folder called /mount/windows, though?

---

