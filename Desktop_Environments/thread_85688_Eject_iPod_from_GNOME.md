---
title: "Eject iPod from GNOME"
date: 2005-11-03
forum: Desktop Environments
---

### Post by kanton on 2005-11-03
I'm looking for a way to use the eject command from the GNOME desktop (just like the way you can do with the cd). The reason is that the iPod mini doesn't recognize the 'unmount' command -- that means that it keeps displaying "Do not disconnect" until i type eject /dev/sda1 in the terminal (it gets unmounted though from Linux though...).
I've tried looking in /etc/hotplug/hotplug.d but the file seems a bit hard for me to grip. Since usb storage devices aren't mentioned in fstab i suppose, I should find the answer in hotplug or maybe the GNOME configuration editor.

This ought to be a quite common annoyance for Linux users with iPods. Somebody who's got the solution for it?

Peter

---

### Post by kanton on 2005-11-03
I'm looking for a way to use the eject command from the GNOME desktop (just like the way you can do with the cd). The reason is that the iPod mini doesn't recognize the 'unmount' command -- that means that it keeps displaying "Do not disconnect" until i type eject /dev/sda1 in the terminal (it gets unmounted though from Linux though...).
I've tried looking in /etc/hotplug/hotplug.d but the file seems a bit hard for me to grip. Since usb storage devices aren't mentioned in fstab i suppose, I should find the answer in hotplug or maybe the GNOME configuration editor.

This ought to be a quite common annoyance for Linux users with iPods. Somebody who's got the solution for it?

Peter

---

### Post by the_purulent on 2005-11-03
My solution was to simply create an eject ipod launcher with 'sudo eject /dev/sda2' in the command section.  Whenever I want to eject I simply click the launcher a couple times. Works fine :)

---

### Post by aysiu on 2005-11-03
This thread may help:

[http://www.ubuntuforums.org/showthread.php?t=56515](http://www.ubuntuforums.org/showthread.php?t=56515)

---

### Post by Ampersand on 2005-11-03
Not entirely sure what you're asking, but you should be able to right click on the drive's icon on the desktop (if it appears) or from the Computer location in nautilus, and select "unmount volume".

Also, you could right click on the desktop, and go to 'new launcher'; and create a launcher with the command
```
eject /dev/sda1
```
(or umount instead of eject might work).

---

### Post by kanton on 2005-11-03
[QUOTE=Ampersand]Not entirely sure what you're asking, but you should be able to right click on the drive's icon on the desktop (if it appears) or from the Computer location in nautilus, and select "unmount volume".

Also, you could right click on the desktop, and go to 'new launcher'; and create a launcher with the command
```
eject /dev/sda1
```
(or umount instead of eject might work).[/QUOTE]

But the iPod doesn't accept "unmount", it needs the "eject" command to be run to be stop displaying "Do not disconnect". I want to run eject directly by right clicking the iPod on the desktop in GNOME, just like i can do with "umount".

Peter

---

### Post by ToastedToad on 2005-11-03
The "eject" command is the only way i have been able to get it to work.

---

### Post by ltmon on 2005-11-03
Ipods _need_ the eject command to be run and it _must_ be run as root.  I haven't found any way around this.

I suggest doing the following for a better ipod experience:

1. Create the file:

/etc/udev/rules.d/10-local.rules

containing the single line:

```

BUS="scsi", SYSFS{model}="iPod            ", KERNEL="sd*", NAME="%k", SYMLINK="ipod"

```

(note the spaces between "iPod" and the closing quote are important.

This will mean that your ipod is always available at /dev/ipod (no matter where it actually mounts e.g. /dev/sda1, /dev/sda2).  Mine seems to move around frequently, and doing this made everything much easier.

2.  Add the following line to /etc/sudoers.  Use "visudo" to edit this file, as the file has permissions and locks that can go wrong if you use a normal editor.

```

ALL     ALL= NOPASSWD: /usr/bin/eject /dev/ipod

```

This means that when you "sudo eject /dev/ipod" you will not be prompted for a password.

You can probably put the following command into a script or button on your gnome panel so you don't have to type anything to remove your ipod.

```

umount /media/ipod && sleep 1 && sudo eject /dev/ipod

```

Cheers,

L.

---

### Post by kanton on 2005-11-05
Thanks for the tip!
I'm confused, though. Shouldn't it possible to eject the ipod by just right clicking on the desktop in gnome? I mean, to let gnome run "eject /dev/sd*" instead of "umount /dev/sd*"? Then you (probably) wouldn't have to change the sudo rights either, since "umount" also demands admin privilegies. I though there would be a quick fix for this, like a new line in the Configuration Editor or something like that.

Peter

---

### Post by NCLife on 2005-12-19
ive tried  "eject /dev/sda2" a couple of times, and in diferent ways and all i get is "unable to open /dev/sda2"  what could i do? :confused:

---

### Post by Hairy_Palms on 2005-12-19
@nclife you need "sudo eject /dev/sda2" if u dont do it as sudo youll get errors like unable to open.
@kanton if u put a script into your home directory so that you can right click in nautilus and have a command called eject ipod that u can run by right clicking anywhere.

---

### Post by raptorNL on 2005-12-21
One way around the problem of the iPod only being ejectable by root, is to simply give /usr/bin/eject root privileges (chmod +s). Giving a program root privilges can of course introduce a security risk, but I think in this case, that risk is extremely small.

The advantage of this being, that Gnome (tested on 2.12.1) will now correctly eject your iPod when you tell it to unmount, disappearing the 'Do not disconnect' message on the iPod.

It should also be possible to rename /usr/bin/eject, substitute it with a small shell script which checks what is being ejected, and if it is an iPod, use sudo to eject it. That should also do the trick just as well.

---

### Post by jbmalone on 2005-12-21
sudo /usr/bin/eject /dev/sda2 is what finally worked to me.

---

### Post by Merak on 2005-12-21
well i've the same problem....let me see if it works for me :P

---

### Post by raptorNL on 2005-12-21
[QUOTE=raptorNL]It should also be possible to rename /usr/bin/eject, substitute it with a small shell script which checks what is being ejected, and if it is an iPod, use sudo to eject it. That should also do the trick just as well.[/QUOTE]
Well, it is and it does. :) I renamed /usr/bin/eject to /usr/bin/eject_orig, and created a shell script /usr/bin/eject that contains the following:
```
#!/bin/sh
if [ "$1" = '/media/ipod' ]; then
	sudo /usr/bin/eject_orig /dev/ipod
elif [ "$1" = '/dev/ipod' ]; then
	sudo /usr/bin/eject_orig /dev/ipod
else
	/usr/bin/eject_orig $1
fi
```
In my sudoers file:
```
[...]
%admin ALL= NOPASSWD: /usr/bin/eject_orig /dev/ipod
[...]
```
Works like a charm. :cool:

---

### Post by Merak on 2005-12-21
ok, sudo eject /dev/sdb works fine for me..
i think i'll type it :P

---

### Post by NCLife on 2005-12-29
ive tried sudo eject /dev/sda2 and sudo /usr/bin/eject /dev/sda2, i still keep getting the same message "unable to open `/dev/sda2'"  
 i wanted to do the script, but i think it will be the same :(

---

### Post by raptorNL on 2005-12-29
[QUOTE=NCLife]i still keep getting the same message "unable to open `/dev/sda2'"[/QUOTE]
You sould'n try to eject **/dev/sda2**, but **/dev/sda**. You don't want to eject a partition, but the whole device. ;)

By the way, to get an iPod assigned the block device **/dev/ipod**, drop the following line in your **/etc/udev/udev.rules**, under **SCSI devices**:
```
[...]
# SCSI devices
BUS=="scsi", SYSFS{model}="iPod*", NAME="ipod"
[...]
```

---

### Post by NCLife on 2005-12-31
i tried as you said, and i got the same error message, "unable to open `/dev/sda'"
  I put the line on the scsi devices, thanks for that tip. So now, instead of /dev/sda i can type /dev/ipod? or what does it do :p 

 Sorry to bother so much, but ive been going around that problem the whole week and i cant get any answers

---

### Post by raptorNL on 2005-12-31
[QUOTE=NCLife]I put the line on the scsi devices, thanks for that tip. So now, instead of /dev/sda i can type /dev/ipod? or what does it do :p[/QUOTE]
That's exactly what it does. :)

If this is not working for you, something else must be wrong, because both on my PC and a friend's PC this works like a charm.

---

