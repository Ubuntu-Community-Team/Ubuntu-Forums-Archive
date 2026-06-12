---
title: "Missing Plugin?"
date: 2009-02-22
forum: General Help
---

### Post by RedSingularity on 2009-02-22
I am trying to view videos on you tube but there are some problems.  Sometimes the video doesnt even play.  Other times it plays but there is no sound.  Am i missing a video plugin for firefox or something?  Any recommendations?

---

### Post by panaut0lordv on 2009-02-22
Running
```
sudo apt-get install ubuntu-restricted-extras
```
in terminal should make the thing ;)
If sometimes it's white where should be video, restart firefox and it'll load right.

Sometime pulseaudio is in conflict with audio (NORMALLY IT SHOULD BE OK, BUT IF YOU WANT TO TRY:
the workaround is
```
sudo apt-get install esound
```
```
sudo apt-get remove pulseaudio
```

---

### Post by RedSingularity on 2009-02-22
Ok i will do that.  By the way....is there something wrong with Adobes latest flash player?  Everything seemed to work fine with the older one.

---

### Post by RedSingularity on 2009-02-22
Well those sound drivers did the trick!  Thanks a lot!!

---

