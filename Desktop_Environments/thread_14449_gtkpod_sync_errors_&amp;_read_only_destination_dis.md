---
title: "gtkpod sync errors &amp; read only destination disk"
date: 2005-02-07
forum: Desktop Environments
---

### Post by mattack on 2005-02-07
Somehow my iPod has become read only...
I was having trouble syncing MP3s to it via gtkpod, getting the following errors:
```

Could not open file "/media/sda2/iPod_Control/Music/F11/gtkpod01879.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F12/gtkpod01880.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F13/gtkpod01881.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F14/gtkpod01882.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F15/gtkpod01883.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F16/gtkpod01884.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F17/gtkpod01885.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F18/gtkpod01886.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F19/gtkpod01887.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F00/gtkpod01888.mp3" for writing.
Could not open file "/media/sda2/iPod_Control/Music/F01/gtkpod01889.mp3" for writing.
```

I decided to try and copy a file to it as an external HDD for giggles and got the following error:
```
**Error while copying to "/media/sda2".**
The destination disk is read-only.
```

I googled a bit and  tried fsck.msdos /media/sda2 with various arguments (mostly -a) but it all returns the same result:
```
dosfsck 2.10, 22 Sep 2003, FAT32, LFN
open /media/sda2:Is a directory
```

My fear is that this is related to my earlier unmounting question. No matter how I unmount my iPod it still says "Do not disconnect." I've been unmounting it by right-clicking the sda2 icon on my desktop, going to "Unmount volume" and then just unplugging it.
Ha...  and now I'm getting the error 
```
**Unable to unmount the selected volume.**
umount: /media/sda2: device is busy
umount: /media/sda2: device is busy
Error: umount failed
```


Anyone have any ideas?
I'm pretty much a Linux n00b.
Any help would be appreciated...

---

### Post by mattack on 2005-02-07
of course now it's working....
i shut down, unplugged the ipod, started the computer, and plugged in the ipod and everything works as it should...  wierd.

---

### Post by mattack on 2005-02-19
I had this same error again today... only now I still can't sync my iPod.
anyone have any clue why this happens?

Is there a way to consistantly unmount an iPod without errors of any kind?

---

### Post by bibo on 2005-02-21
i've had the same problem with my 4th gen ipod.
it's worked fine in the past and i have synced it many times.

however today it decided to become a read-only file.

i thought it may have something to do with permissions which are currently set up on the sda3 folder as 744.  it doesn't register me as the owner of the folder and thus i am not able to write to it as only the owner can do that.

i find this strange because i am the owner and the permissions it indicates that.  for some reason though it still doesn't believe that i'm the owner and says i can't change permissions.  i don't understand why there is a contradiction.

  i tried to change the permissions using:  

sudo chmod -R 755 bibo /media/sda3 

but that didn't work.

have you been able to figure it out yet? does anybody else know? what information do you need from me?

if i do find out...i will post it here.

---

### Post by bibo on 2005-02-21
i forget to mention that if you umount thru root you should be okay. 

what i do is:

eject /media/sda3

if this doesn't work you may have to kill process famd if it's running

lsof | grep sda3

is famd there?

sudo killall -HUP famd

then try to eject /media/sda3 (or wherever your ipod is)

it should work now...

but it has been a while since you posted...you probably figured it out by now.  if there is a better way...please let me know.

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=mattack]
Is there a way to consistantly unmount an iPod without errors of any kind?[/QUOTE]

Yep. Use the default Ubuntu fstab (if you want I'll post it here), and tell GTKpod to handle the mounting of the Ipod. Works like a charm for me.

---

### Post by mattack on 2005-02-21
what I've settled on is eject -m /media/sda2

that seems to work no matter what. it still returns the error:
```
matt@mattack:~ $ sudo eject -m /media/sdb2
eject: unable to eject, last error: Invalid argument
```
I'd like it if it didn't return an error. the iPod does say it's okay to disconnect after that though...

also my iPod has made a switch from sda2 to sdb2...
anyone know what gives with that?

---

### Post by astoltz on 2005-02-21
[QUOTE=mattack]also my iPod has made a switch from sda2 to sdb2...
anyone know what gives with that?[/QUOTE]
Do you have another USB stoage device plugged in?  Or if the ipod didn't get unmounted properly, the /dev/sda2 node may still exist.  

I made a udev rule for my ipod so it always gets /dev/ipod which has solved the problem of it getting sda / sdb depending on what else is attached to the usb bus at the time.  Check out [this link](http://www.reactivated.net/udevrules.php) for a good udev rule howto.

---

### Post by mattack on 2005-02-22
[QUOTE=astoltz]Do you have another USB stoage device plugged in?  Or if the ipod didn't get unmounted properly, the /dev/sda2 node may still exist.  

I made a udev rule for my ipod so it always gets /dev/ipod which has solved the problem of it getting sda / sdb depending on what else is attached to the usb bus at the time.  Check out [this link](http://www.reactivated.net/udevrules.php) for a good udev rule howto.[/QUOTE]

I didn't have another USB storage device plugged in but had just unmounted my USB thumb drive...  okay, I get it.

I looked at the link and wrote my own udev rule which doesn't seem to work. Here it is:
# my custom ipod rule
BUS="usb", SYSFS{model}="iPod", Name="%k", SYMLINK "ipod"

the SYSFS{model}="iPod" bit I got from the output of udevinfo -a -p /sys/block/sda

I put the rule in the section of USB devices, first in the list.
Is there something I'm missing?
What does your rule say?

---

