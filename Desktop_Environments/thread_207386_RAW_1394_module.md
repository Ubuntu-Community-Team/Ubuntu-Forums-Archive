---
title: "RAW 1394 module"
date: 2006-07-01
forum: Desktop Environments
---

### Post by ColinG on 2006-07-01
The raw 1394 module is not available to me when I start Ubuntu. Hence I cannot capture video via Kino. 

Some helpful advice via this forum indicates this is a permission problem that is overcome if I execute sudo chmod 777 /dev/raw/1394.This is absolutely true but the command does not stick and has to be executed each time I boot the os,

Is there a way to make this chmod command permanent?

Thanks
Colin

---

### Post by hoodwink on 2006-07-02
[QUOTE=ColinG]The raw 1394 module is not available to me when I start Ubuntu. Hence I cannot capture video via Kino. 

Some helpful advice via this forum indicates this is a permission problem that is overcome if I execute sudo chmod 777 /dev/raw/1394.This is absolutely true but the command does not stick and has to be executed each time I boot the os,

Is there a way to make this chmod command permanent?

Thanks
Colin[/QUOTE]
One simple say is to put the command in /etc/rc.local which is the last bootup script run before starting the gui session. You don't need sudo here, since rc.local runs as root.

You could also set a udev rule, but someone else will have to help with that.

---

### Post by ColinG on 2006-07-02
Thanks for this but I can't find an /etc/rc.local. What am I missing:confused: 

Many thanks for the help
Colin

Ah, update, found it buit it does not seem to have any effect. The mod seems to be ignored and I still have to use the terminal. Below is my rc.local 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
chmod 777 /dev/raw1394
exit 0

---

### Post by ColinG on 2006-07-02
A bit more info - it seems the 1394 module is not loaded at boot but rather when the ieee device is actually plugged in. As such the chmod command does not work until I have Kino running and my camera plugged in. 

That would explain why the rc.local approach fails and why any attemp to run chmod via the terminal brings the error no such file or directory - the file or directory is not present until the conditions outlined in my above papagraph are met.

I suspect this is all tied backm to hot-plugging.

Any idead :confused: 

Thanks
Colin

---

### Post by tomchuk on 2006-07-02
Just make sure you're in the 'disk' group and you shouldn't have any permissions problems. From /etc/udev/rules.d/40-permissions.rules:
```

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",          GROUP="disk"
KERNEL=="dv1394*",          GROUP="video"
KERNEL=="video1394*",           GROUP="video"

```
If you wanted to have write permissions for everyone (insecure) you could add the line, but I wouldn't recommend it:
```

KERNEL=="raw1394",          MODE="0666"

```

---

### Post by ColinG on 2006-07-02
Here is my udev rule:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",          GROUP="disk"
KERNEL=="dv1394*",          GROUP="video"
KERNEL=="video1394*",           GROUP="video"

The situation however remains then same and I still have to enter the sudo chmod command via a terminal. 

I am a bit of a nube (well more than a bit actuially :( ) so I could be missing something. For instance, how do I ensure I'm a member of the disk group. I cannot find such a group using the "users and groups" functionality under System, Administration.

Thanks for helping me on this. I know entering the chmod command is no big deal but somehow it seems wrong to me. The system should pick up the device automatically imo.

Many thanks
Colin

---

### Post by tomchuk on 2006-07-02
You can add yourself to the disk group by issuing the following command in a terminal:
```

sudo usermod -aG disk $USER

```
Next reboot you'll be a member of the disk group and will have read/write permissions to the raw1394 device.

---

### Post by ColinG on 2006-07-02
[QUOTE=tomchuk]You can add yourself to the disk group by issuing the following command in a terminal:
```

sudo usermod -aG disk $USER

```
Next reboot you'll be a member of the disk group and will have read/write permissions to the raw1394 device.[/QUOTE]

Excellent stuff, tomchuk - that's sorted it\\:D/ 

Many,. many thanks.

Incidentally do you know why the disk group does not show in Users & Groups?
Thanks agail
Colin

---

### Post by tallpaul100 on 2008-02-23
> **tomchuk said:**
> You can add yourself to the disk group by issuing the following command in a terminal:
```

sudo usermod -aG disk $USER

```
Next reboot you'll be a member of the disk group and will have read/write permissions to the raw1394 device.

Just like to say this worked for me too. I'm using a canon MV890 connected with firewire 1394 pci card.
Kino wouldn't see the device to be able to capture from it. but now it works thanks to tomchuk. Cheers.

---

### Post by anuban on 2008-02-26
> **tallpaul100 said:**
> Just like to say this worked for me too. I'm using a canon MV890 connected with firewire 1394 pci card.
Kino wouldn't see the device to be able to capture from it. but now it works thanks to tomchuk. Cheers.

> **tomchuk said:**
> You can add yourself to the disk group by issuing the following command in a terminal:
```

sudo usermod -aG disk $USER

```Next reboot you'll be a member of the disk group and will have read/write permissions to the raw1394 device.

This works for me too.  I have a Sony DCR-HC32.
Thanks a lot.  How do you guys get these kind of things....

Thanks again..
Anurag:guitar:

---

