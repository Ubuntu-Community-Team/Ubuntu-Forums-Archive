---
title: "How to umount &quot;busy&quot; Samba-connection?"
date: 2006-01-17
forum: General Help
---

### Post by pbb on 2006-01-17
I've got a Samba-connection to my other computer, mounted as /media/foo.

After I turned off that other computer, I was not able to umount the share anymore. Typing "sudo umount /media/foo" was answered with "umount: /media/foo: device is busy".

This is really annoying, every time I open the /media folder in Nautilus, I need to wait for two minutes before I can continue!

Is there a way to unmount that share, without restarting that or my computer?

---

### Post by slashem on 2006-01-17
sudo fuser -km /media/foo
sudo umount /media/foo

HTH. :)

---

### Post by pbb on 2006-01-17
No, that doesn't work either:

```
$ sudo fuser -km /media/foo
/media/foo: Input/output error
/media/foo: Input/output error
$ sudo umount /media/foo
umount: /media/foo: device is busy
umount: /media/foo: device is busy
```

---

### Post by maglis on 2006-01-17
[quote=pbb]"umount: /media/foo: device is busy".
[/quote] 
I use sudo umount -l /mount/point

try man umount

> -l     Lazy unmount. Detach the filesystem from the filesystem  hierar&#8208;
              chy now, and cleanup all references to the filesystem as soon as
              it is not busy anymore.  (Requires kernel 2.4.11 or later.)

---

### Post by pbb on 2006-01-17
I ended up restarting my computer, the waiting time every time got really on my nerves. I will try this way next time I run into this.

---

### Post by pbb on 2006-01-17
I ended up restarting my computer, the waiting time every time got really on my nerves. I will try this way next time I run into this.

---

