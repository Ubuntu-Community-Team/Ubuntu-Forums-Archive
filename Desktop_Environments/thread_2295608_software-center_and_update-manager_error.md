---
title: "software-center and update-manager error"
date: 2015-09-20
forum: Desktop Environments
---

### Post by biji on 2015-09-20
Hi..
Software-center and update-manager can not work properly on my system (Ubuntu gnome 15.04)

When I run from console, get this error:
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program org.debian.apt: Success

checked dbus and systemd tried to call org.debian.apt, but the error is not clear: **Success**

When I run /usr/sbin/aptd manually using root, software-center run again normally

Please help.. Thanks

---

### Post by jean_rivire on 2015-09-21
Hi,

Could it be that the permissions of the applications are somehow been modified? (since you can excecutate in root, it looks af if you need to go to /applications -should be in /etc I think- and see properties of software center and update manager; are they in read-only for you ? if that's the case, just change that to read and write and make sure the box that says 'this programm is excecutable' is checked;

Cheers,

---

### Post by Sweet_Baby_Jamie on 2015-09-21
You need to be root when adding, removing, or updating software!  Just use sudo when opening it in the terminal.  Or open Synaptic Package Manager (which requires root password to open).  I only use Synaptic to update but that's just my preference

---

### Post by coffeecat on 2015-09-21
> **Sweet_Baby_Jamie said:**
> You need to be root when adding, removing, or updating software! 

Ouch! No you don't. You need to be in the administrator account and need to temporarily elevate your permissions with your admin account password. The root account is disabled by default in Ubuntu and its official variants.   

> **Sweet_Baby_Jamie said:**
> Or open Synaptic Package Manager (which requires root password to open).

No it doesn't! As above. Anyone needing to run Synaptic should open it from the dash or launcher bar or menu, depending on their desktop environment, and then provide their **admin account** password when prompted to do so.

Please see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by biji on 2015-09-21
Thats right.. it's because wrong permission/owner of file modified....... omg I just rsync my / to new laptop and this happen

This file owner is root.fuse should be root.messagebus:
/usr/lib/dbus-1.0/dbus-daemon-launch-helper

Thanks all

---

