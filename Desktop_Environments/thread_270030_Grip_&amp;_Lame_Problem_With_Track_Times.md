---
title: "Grip &amp; Lame Problem With Track Times"
date: 2006-10-02
forum: Desktop Environments
---

### Post by bgeek on 2006-10-02
Hi all,

I've installed Grip 3.3.1 and Lame via the repositories.  I rip audio CD's using the Grip (cdparanoia) option and then encode using the Lame command: -V 0 --vbr-new %w %m

However, there appears to be a problem with every CD I have tried to rip & encode - the track times are out on every mp3 in XMMS.  The track times can be in the range of 20 to 30 minutes, when the actual length is 3 or 4 minutes.  If a track is played then the times are instantly corrected.

I have also built a deb of the latest stable of Lame (3.97), but the problem still exists.  

Is this likely to be a Grip problem or XMMS? Or does anyone have any other experiences of this problem?  The tracks work fine on my hardware based mp3 player.

Cheers,

Gerald

---

### Post by NESFreak on 2006-10-11
me to. Trying to get some of my in flac encoded pinkfloyd albums on my mp3 player. did ```
flac -d *.flac
lame --preset extreme --nogap *.wav #best vbr, but i end up with Signs Of Life more than 35 minutes long. So i thought must me the vbr. tried cbr.
lame --preset 256 --nogap *.wav #same story. so i did CBR
lame --preset insane --nogap *.wav #wich does work, but results in big files, resulting in my mp3player to cash more often wich (for a harddrive player isn't what you want.
```

this is really weird. Someone? BTW the problem is LAME.

NESFreak

---

### Post by NESFreak on 2006-10-11
maybe this bugreport will help [https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10/+bug/35112](https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10/+bug/35112)

NESFreak

---

