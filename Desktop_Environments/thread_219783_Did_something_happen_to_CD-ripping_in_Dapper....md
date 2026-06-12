---
title: "Did something happen to CD-ripping in Dapper...?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by aysiu on 2006-07-20
In the past two releases (Breezy and Hoary), I've had absolutely no problems with CD-ripping. For some reason, yesterday I had a really hard time ripping CDs to MP3 in Dapper.

I tried several applications and none seemed ideal:

**KAudioCreator**: It was just deathly slow, and I tried both CD-ROM drives. I mean... it was taking well over a half hour to rip one song. It wasn't like this in Breezy.

**Goobox**: Wouldn't do the CDDB lookup, so I ended up with a bunch of unnamed songs. Does anyone know a way to force Goobox to do a CDDB lookup?

**Sound Juicer**: I tried [this fix](http://www.ubuntuforums.org/showpost.php?p=749491&postcount=3) to get MP3 ripping, but when I ripped them, they came out really weird... just some weird sharp noises--no actual music. Also, none of the ID3 tags populated.

**abcde**: There are some command-line utilities that I just love (*mogrify*, *aptitude*, and *rsync*), but I couldn't make head or tails of the *abcde man* page.

**grip**: Turned out to be my best option. The configuration was a bit confusing (a *lot* of tabs), but it worked. One annoyance was that it appeared I had to manually select each track to be ripped (unlike the other ripping programs that would allow you to select all songs at once).

I guess I'm sticking with Grip for now. Am I the only one experiencing this? Is my computer a freak? I don't think it is, since these applications were all behaving with Breezy and Hoary. Anyone have similar experiences? Anyone know how to fix Goobox or Sound Juicer? Are there special tricks to speeding up KAudioCreator or making Grip select all tracks?

---

### Post by reacocard on 2006-07-20
Here's my sound juicer gstreamer pipeline. No idea if it will fix anything but it's worth a shot:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 bitrate=160 ! xingmux ! id3v2mux
```

I used to have trouble with tags not working in sound juicer as well. The id3v2mux part fixes that problem. I also increased the bitrate (from 128 to 160), enabled vbr for better audio quality, and used xingmux for tag compatibility with newer players.

---

### Post by aysiu on 2006-07-20
Thanks for the quick reply. I'll play around with that--see if it makes a difference.

---

### Post by aysiu on 2006-07-20
No. Tried it out--same problem--scratchy sounds instead of music and no ID3 tags written.

Is something wrong with my Sound Juicer?

**Edit**: Okay. Apparently, I had to install *gstreamer0.10-plugins-ugly-multiverse* to get the encoding to actually work (music instead of weird noises).

It's still not writing ID3 tags, though...

Well, if it's not an easy fix, I suppose I can just stick with Grip for now.

---

### Post by DoktorSeven on 2006-07-20
grip is my preferred ripping app.  Lots of initally confusing options but gives you a lot of power.

By the way, if you want to rip the entire CD, just go to Rip tab and hit Rip+Encode with no tracks checked; it'll ask you if you want to rip the whole CD.

---

### Post by aysiu on 2006-07-20
Good tip about the *Rip+Encode*. Thanks, DoktorSeven.

---

