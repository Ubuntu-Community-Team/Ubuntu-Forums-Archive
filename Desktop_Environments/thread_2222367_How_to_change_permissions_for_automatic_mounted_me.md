---
title: "How to change permissions for automatic mounted media"
date: 2014-05-06
forum: Desktop Environments
---

### Post by juray2 on 2014-05-06
Hello,


i have serious problem  with writing udev rules for USB drives. It seems, they are simply  ignored. My Xubuntu 12.04 mounts USB drives to  '/media/<name_of_drive>' with permissions 'drwx------'. The owner  and group of that directory is currently logged in user and his default  group.


I would like to acheive with udev rules, that file permissions will be 'drwxr-xr-x'.


This post not work for me
[http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive/17550#17550](http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive/17550#17550)


It is strange, that I cannot change permissions with chmod (either as user or root).



Another strange thing - following this documentation

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)


the drives should be automounted to '/media/<user>' directory, not only to '/media', like in my case.


I spent few hours with this problem and i cannot find solution or only explanation.


Thak you for help.[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

---

### Post by ian-weisser on 2014-05-06
Please show us the udev rule that isn't working.

---

### Post by Dennis N on 2014-05-06
> Another strange thing - following this documentation
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
the drives should be automounted to '/media/<user>' directory, not only to '/media', like in my case.

An explanation for this part of your post:

Xubuntu 12.04 (or any other 12.04) uses **udisks** to automount USB devices and mount to **/media**
Releases after 12.04 use **udisks2** and mount to **/media/<username>**

---

### Post by juray2 on 2014-05-07
Thank you for answers.

As a rules i've tried several combinations of udev rules like:

```
# UDEV Rules to change the permission of USB disks
#
# Source: http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive/17550#17550 

#KERNEL=="sd*[0-9]", ATTR{removable}=="1", ENV{ID_BUS}=="usb", MODE="0666"
KERNEL=="sd?[0-9]", SUBSYSTEM=="block", MODE="0666"
```

---

### Post by ian-weisser on 2014-05-07
I don't quite understand - are you trying to fix a problem of disks mounting with root-only permissions instead of user permissions, or are you trying to mount disks with a custom permission?

---

### Post by juray2 on 2014-05-07
I need to mount removable media automatically with permissions 'drwxr-xr-x' or 0755 for directories ('rwxr--r--' for files).

Now, after insetring USB Flash drive, or SD card, ... they are automaic mounted with default permissions 'drwx------' or 0700 for directories. So only logged in user can read the files from removable device.

The aim is to allow single user work with desktop PC (write emails, administrative wrok, ...) while the other users will be able to use its memory card reader, for read and copy the content of xD-Picture Card with photos, using ssh (sftp). I like to acheive that without switching users.

---

### Post by Morbius1 on 2014-05-10
Until someone comes around with udev rules experience give this a shot:

Install bindfs:
```
sudo apt-get install bindfs
```
Create another mount point:
```
sudo mkdir /ExtDisks
```
Temporarily bind(fs) the /media directory to the new mount point with a new set of permissions:
```
sudo bindfs -o perms=0644:+X /media /ExtDisks
```
What should happen is that when the usb device is inserted it will mount in two different locations simultaneously: 

One at /media/LABEL with permissions of 700
And again at /ExtDIsks/LABEL with permissions of 755

The user who inserted the usb device can continut to use it at it's default location in /media and everyone else can use the other location of /ExtDisks.

[COLOR=#0000cd]Now as Uncle Ben ( Spider-Man's uncle not the rice guy ) once said: With great power comes great responsibility.
The system uses /media to auto mount a whole host of things some of which you might not want to have with these new permissions so you need to be careful with this. If for example you have an internal partition that you don't have mounted in fstab when you mount it through the file manager it also ends up in /media and that too will have these permissions.[/COLOR]

If it works the way you want it you can have it bind automatically at boot by adding the line ( without sudo ) above the "exit 0" line in /etc/rc.local.

If the temporary mount doesn't do what you want just unmount it:
```
sudo umount /ExtDisks
```

---

### Post by juray2 on 2014-05-29
it works. it is good solution for us. thank you!

---

### Post by mörgæs on 2014-05-29
Good, please mark the thread 'solved'.

---

