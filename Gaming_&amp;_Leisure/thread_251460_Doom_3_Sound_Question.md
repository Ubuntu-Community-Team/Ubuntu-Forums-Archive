---
title: "Doom 3 Sound Question"
date: 2006-09-05
forum: Gaming &amp; Leisure
---

### Post by Dark Elitist on 2006-09-05
Hey everyone!

I just converted another friend to Linux, specifically Kubuntu 6.06.1.  His sound card isn't a Creative so he is having the infamous "sound doesn't work when launching Doom 3 / ET / RTCW / etc."

In order for sound to work, I had to change the in-game settings from "best" to "oss".  Launching the game requires:

```
sudo -s
sudo echo "doom3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
doom3
```

Sound works then until the game is closed.  For sound to work 100% properly in other applications, the following needs to be typed:

```
sudo -s
sudo echo "doom3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

Now, I had a friend with this identical problem a while back and it was fixed by adding the following code to the bottom of some file with gedit:

```
# Doom 3 Sound
sudo -s
sudo echo "doom3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
sudo echo "doom3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

Then, on reboot, sound always switches priority automatically from on to off.  I just don't remember the name of the file to edit, or its location.  Could somebody please refresh my memory?

Thanks!

---

### Post by Dark Elitist on 2006-09-06
Does anybody know?  It is really easy, I just don't remember the file!  I think it was something in /etc/init.d/. Come on fellas!

---

