---
title: "controling sound in ubuntu"
date: 2008-03-31
forum: Desktop Environments
---

### Post by Empire666 on 2008-03-31
I have a laptop running ubuntu and control it from the command line.
What I'm having trouble with is being able to mute the sound on it when needed. I have looked around and found that gnome-volume-manager + gnome-volume-control , and tried the commands "gnome-volume-manager --disable-sound" and "gnome-volume-control --disable-sound" but failed in that attempt.
One thing I did find that works is "nircmd.exe mutesysvolume 1" in wine to mute the volume in ubuntu and "nircmd.exe mutesysvolume 0" to enable it, but I dont want to have to use wine to mute the sound.

So my problem is that I would rather use a native ubuntu command to mute the sound.

any suggestions?

---

### Post by Empire666 on 2008-04-02
up

---

### Post by rashead on 2008-04-03
I'm kind of new to all this...

but, you can go into terminal and type "alsamixer" (without the quotes) which will bring up a mixer type of interface.  you can use the right and left arrows to select the area you want and hit the "m" key to mute and unmute each one.

Hope that helps

---

### Post by mali2297 on 2008-04-03
To toggle mute/unmute, you can use
```

amixer set Master toggle

```

---

