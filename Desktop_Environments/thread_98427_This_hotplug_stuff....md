---
title: "This hotplug stuff..."
date: 2005-12-03
forum: Desktop Environments
---

### Post by xmastree on 2005-12-03
I have a card reader, which usually works fine but occasionally gets stuck. I plug in my CF card and it doesn't mount. Sometimes, disconnecting the reader and reconnecting will make it work, sometimes not.
A reboot will always fix it, but is there a better way?

Is there some command I can run to refresh the whole thing without rebooting?

---

### Post by xmastree on 2005-12-05
Bump.

It's doing it again... :-(

---

### Post by 23meg on 2005-12-05
```
sudo mount -a
```

---

### Post by xmastree on 2005-12-06
Nope, that didn't help. I thought **mount -a** just mounts what's listed in fstab? :confused:

This is a CF card, in a reader connected to a USB port. lsusb shows the card reader connected.

---

### Post by schdefan on 2005-12-08
[QUOTE=xmastree]Nope, that didn't help. I thought **mount -a** just mounts what's listed in fstab? :confused:[/QUOTE]

that is correct. mount -a Mount all filesystems (of the given types) mentioned in fstab.

[QUOTE=xmastree]
This is a CF card, in a reader connected to a USB port. lsusb shows the card reader connected.[/QUOTE]
You can mount usb devices with e.g.
```
mount -o users,rw /dev/sda1 /mnt/cardreader
```
I haven't found out how one can see if the device can be mounted on sda1 or sdb2, etc.
create the directory /mnt/cardreader the option users,rw is for non-root users.

schdefan

---

### Post by xmastree on 2005-12-09
Thanks, but it seems I found a more elegant (as in easy) solution [here]("http://www.ubuntuforums.org/showthread.php?t=100297") ```
sudo /etc/init.d/hotplug restart
```Seems to do something, but since it hasn't locked up recently I can't say for sure.

Not that I'm upset about it not locking up of course. :cool:

---

