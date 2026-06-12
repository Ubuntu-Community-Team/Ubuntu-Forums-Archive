---
title: "Where has the Disks Menu gone?"
date: 2006-11-21
forum: Desktop Environments
---

### Post by IanVaughan on 2006-11-21
Im sure on Dapper there was a nice menu under System->Administration, called "Disks", that allowed you to see what disks was on your system, and mount etc them.
But having just done a clean install of Edgy, its not there?
At the command line no disk* command seems to be obvious!

---

### Post by eeGhoong0ais on 2006-11-21
I'm still on Dapper, and you're right, there is such a thing as System > Administration > Disks. It's associated with the command ```
gksu disks-admin
``` - obviously I don't know if disks-admin is still in Edgy.

---

### Post by stef70 on 2006-11-21
You can get a list of all drives via the "Computer" window in Nautilus (available from the Places menu in Gnome 2.16). 

The command lines are mount & umount for the root user or pmount & pumount for regular users.

Be aware that pmount will probably only works on hot-plugable devices (cdrom, usb-key, ...).

I am not aware of any commands to list the available drives. The best I can think of is lshal but its output is a bit cryptic. 

And of course, there is always the possibility to use the DriveMount applet. 

You may also want to have a look at the fuse packages that allows regular users to mount their own filesystems:
 - sshfs to mount remote ssh accounts.
 - encfs to mount encrypted files
 - fusesmb to mount SMB shares
 - ...

---

### Post by IanVaughan on 2006-11-21
> **Etiol said:**
> I'm still on Dapper, and you're right, there is such a thing as System > Administration > Disks. It's associated with the command ```
gksu disks-admin
``` - obviously I don't know if disks-admin is still in Edgy.

Well, thanks for finding and confirming that it was there!
But that command does not exist on Edgy!
Why remove something I thought was good, is there something better in its place?

Any btw :
```
sudo fdisk -l
```
lists all the drives as well.

---

### Post by guyforget on 2006-11-24
I was just looking for this  as well.  How come it was taken out, good tool, IMO.

---

### Post by not_cool on 2006-11-25
You can always add the disk mounter to the gnome panel.

---

### Post by dcstar on 2006-11-26
> **not_cool said:**
> You can always add the disk mounter to the gnome panel.

I seem to recall that you can edit the preferences somewhere in Edgy to re-add various things back into the menus (cannot recall exactly where....)

It looks like some things were taken off the menus to "simplify" things for users.................

---

### Post by mgmiller on 2006-11-26
My understanding is that the disks admin was removed completely.  It had not been maintained for some time and the gnome people removed it.  There is no entry available from the System>Preferences>Menu Layout either.  You could try using synaptic to install gparted.  See if that gives you the functions you need.

---

