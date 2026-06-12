---
title: "windows codecs"
date: 2006-06-14
forum: Desktop Environments
---

### Post by nickdr on 2006-06-14
it seems that after i installed xgl/compiz my windows codecs "sorta" stopped working. i get the audio fine, but the video is messed up (imagine setting your refresh rate too high- thats what the video looks like) even if i shut off xgl/compiz i am still getting this. i tried to reinstall the codecs but i was still unsuccesful, anyone got a fix for this??

thanks

---

### Post by TigerWolf on 2006-06-14
This should install most codecs

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-main1 libxine-extracodecs
```

---

### Post by nickdr on 2006-06-15
i have all the codecs, and at on point they all worked. i am wondering if anyone has found a fix for xgl causing distortion

---

### Post by Joeb on 2006-06-15
I had a similar experience.  Lost my tv card output, too.  To fix it, I first had to go back to undo all the changes I made for the xgl/compiz and go back to the nv driver.  After rebooting, things were back to working.  However, switching back to the nvidia driver, things were still broke.  Telling synaptic to reinstall the nvidia driver solved that.  I decided to live without the xgl/compiz since everything else was working.

---

