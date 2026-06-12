---
title: "What's my iPod's device name?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-06-04
Since upgrading to Dapper, I've not been able to automount my iPod.  I think lots of people have experienced this.

Following these instructions: [http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu), I've edited my fstab...but I'm fairly sure that I need a different device name (probably sda2)

Can someone please remind me of the terminal command that shows me what's where.

And - in general - can anyone point me towards info. on how to mount devices?  I can't fid it easily in the documentation.

---

### Post by shrift on 2006-06-04
You can use ```
sudo fdisk -L
``` to display all disks attached to your system. That should help you find your ipod.

As for mounting things, I would read the manual of the "mount" command. So: "man mount" in a terminal. It is pretty easy. Here is an example:

mount -t vfat /dev/sda2 /media/ipod

what we have here is the "mount" command, the -t to specify what kind of filesystem it is, the vfat is attached to that, if you had other options to add, this is wher eyou would do that. For instace "-o" for options then "umask=000" The umask makes windows partitions accesible to normal, non-root, users. AFter the options section is the where you say what is getting mounted, followed by the directory you want it to be mounted in.

---

### Post by Edward The Bonobo on 2006-06-04
vmt.

Has anyone had any luck with the Great Dapper Drake Disappearing Automount Problem?

---

