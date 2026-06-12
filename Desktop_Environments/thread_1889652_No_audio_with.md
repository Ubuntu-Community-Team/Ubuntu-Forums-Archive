---
title: "No audio with"
date: 2011-12-01
forum: Desktop Environments
---

### Post by manolomanolo on 2011-12-01
Hi to all.

I hear no audio in Kubuntu. My story: I installed Ubuntu 11.10 and then I installed the kubuntu-desktop package.
After a while in which I could hear audio, now I can hear audio anymore.
What can I do?
thanks.
Regards.

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

---

### Post by staf0048 on 2011-12-02
I'm not running Kubuntu, but I ran into the exact same issue 3 days ago.  My audio just stopped working.  

What fixed it was this:

Go to Sound Preferences, go to the Hardware tab, set Profile to "off" is was on "Digital Stereo (HDMI) output" and my audio instantly worked again.

Hope that helps lead you to a solution,

Good luck!

---

### Post by kio_http on 2011-12-02
Check if it is muted in alsamixer

Try

```
sudo apt-get purge alsa-base pulseaudio
```

and 

```
sudo apt-get install alsa-base pulseaudio
```

---

