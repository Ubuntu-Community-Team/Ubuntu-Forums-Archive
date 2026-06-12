---
title: "USB Automount won't.  Will on bootup."
date: 2006-01-11
forum: Desktop Environments
---

### Post by Karst on 2006-01-11
Problem:  The automount feature on Breezy doesn't work for me when I try to mount my Nokia 770.  (It looks like a thumb drive, size depends on the card I have in it).

When I boot it with the USB plugged in, it recognizes the device fine, makes me a device named the same name I give my RS-MMC chip in the Noika, and I can use it fine.  To make sure it's all written, I 'sync' before removing the USB cord. (when I didn't sometimes got truncated files).  The icon and /dev/sda1 both disappear and in the /var/log/messages, I see that it shows a usb disconnect.  When I plug it in, nothing happens.

Hoary works fine with this device (mounts and unmounts fine.)

Oh, lsmod shows usb_storage installed on Breezy after removal, it's gone on Hoary.  Trying 'rmmod usb_storage' on Breezy gives me a "This thing is still in use" error and I can't kill it.  Anyone have any ideas?  I've fallen back to using Hoary for use with my toy, and will try Dapper to see if it works in there.

---

### Post by Mickey Mouse on 2006-01-16
I get nothing, zilch, with my usb card plugin that contains an XD memory card.
It is the first device I tried to plug in after installing ubuntu. I guess I am getting too cocky, expecting something to actually work on linux....

---

### Post by Mickey Mouse on 2006-01-17
More specifically, I have all the right packages but hal sees nothing and does nothing.:(

---

