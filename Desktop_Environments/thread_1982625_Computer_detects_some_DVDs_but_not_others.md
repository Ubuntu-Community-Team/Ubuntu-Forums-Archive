---
title: "Computer detects some DVDs but not others"
date: 2012-05-18
forum: Desktop Environments
---

### Post by Acharn on 2012-05-18
My problem has taken a turn for the worse. I finally found the answer to my problem with VCDs by installing SMPlayer. It seems Movie Player was not able to play VCDs, but SMPlayer (and VLC Player) is. So I have a couple of video DVDs that were burned on this machine when I was still running Windows. One was copied from a commercial video DVD, the othe was "authored" on this machine with DVD Flick and then burned. When I insert either one in the drive it just sits there. With one of them the light keeps blinking, but no matter how long, the drive never reads it.

So I figure, Aha! Must be a software bug. No. It turns out I had some old DVDs of The Sopranos I'd forgotten about. So I stick one in. Not only does the drive detect it, Movie Player plays it! So then I try inserting a blank DVD. Once again, the drive doesn'see it. This is the same batch of DVDs I was using to burn under Windoes with no problem. So I can't save data to a DVD, and I can't retrieve data from DVDs that I burned in this drive, but I can watch old episodes of The Sopranos that I've already seen.

The relevant info from 'sudo lshw -C disk':

```
*-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

```

I surely would appreciate some suggestions about what to try next.

---

### Post by Rodney9 on 2012-05-18
Try the offending discs in another machine.
Make sure they are not dirty or scratched - [http://www.ehow.com/how_2049991_clean-dvd.html](http://www.ehow.com/how_2049991_clean-dvd.html)

Rodney

---

### Post by DMGrier on 2012-05-18
I have had a issue with some disc before and I just assume it is copy right protection.

---

