---
title: "Totem-xine Won't Play DVDs?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by mrgnash on 2005-12-19
Ok I've had this issue for awhile now and haven't been able to find a solution. When I try to play DVDs in Totem I get the following error:

'Failed to find mountpoint for device /dev/hdc/ in /etc/fstab.' Now this doesn't present a problem for Gxine, so what is Totem complaining about? :(

---

### Post by 23meg on 2005-12-19
Can you post the line that corresponds to /dev/etc in your /etc/fstab file?

---

### Post by mrgnash on 2005-12-19
Is this the one?

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by samwyse on 2006-01-01
I get the same error using totem-xine. Kaffeine and Xine plays DVD's, but the video is jerky. DMA is enabled, I don't know what else to try. DVD playback worked fine in Fedora Core.

edit: actually DMA wasn't enabled, now it works. My hdparm.conf had the wrong settings after all :oops: Still the same error in totem-xine though.

---

### Post by teppic on 2006-01-03
Try inserting an audio CD, take out the CD and then it'll be fine with DVDs.

I've reported this as a bug previously - no action as yet.

---

