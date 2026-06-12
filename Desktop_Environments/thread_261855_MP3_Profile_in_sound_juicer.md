---
title: "MP3 Profile in sound juicer"
date: 2006-09-20
forum: Desktop Environments
---

### Post by offramp13 on 2006-09-20
I looked in the sound juicer help files and it told me how to add MP3 as an option to rip in. But what it didnt tell me was that it rips in a 128 kbps bitrate. Does anyone know how to make it so i can rip in 320?

---

### Post by mitch.c on 2006-09-21
> **offramp13 said:**
> I looked in the sound juicer help files and it told me how to add MP3 as an option to rip in. But what it didnt tell me was that it rips in a 128 kbps bitrate. Does anyone know how to make it so i can rip in 320?
Can't get to my PC now, but I think adding bitrate=320 to the gstreamer pipeline will do it. There's a really handy tool that's part of gstreamer0.10-tools. Run this at the command line:
```
gst-inspect-0.10 lame
```This will list all of the parameters exposed by using lame with gstreamer. This should give you all you need to verify the pipeline syntax.

---

### Post by offramp13 on 2006-09-21
thanks man

---

