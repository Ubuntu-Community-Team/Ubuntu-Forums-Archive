---
title: "Sound stopped working for some apps"
date: 2006-08-30
forum: Desktop Environments
---

### Post by linuxpenguin on 2006-08-30
My sound is no longer working in some apps.  For example, it still works just fine in Totem, but it no longer works in Tux-Guitar or when I'm watching Flash videos in Mozilla or Firefox.

Any ideas?

---

### Post by xtknight on 2006-08-30
I know Flash has some weird problems with sound in Linux but maybe that's not your problem.  Type **gstreamer-properties**  Changed anything in there lately?  I think the problem is one program is using ALSA and the other is using OSS and failing for some reason.  Try setting output to OSS in gstreamer-properties and see if Totem still works.  Try ALSA too.

---

### Post by linuxpenguin on 2006-08-30
Thanks, setting it to alsa did the trick!  I didn't play with any of these settings but I did install some codecs - maybe that had something to do with it.

---

