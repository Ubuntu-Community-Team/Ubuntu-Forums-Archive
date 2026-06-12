---
title: "quake4 amd64 without chroot"
date: 2005-11-01
forum: Gaming &amp; Leisure
---

### Post by yqiang on 2005-11-01
Hey guys, I've finally managed to get quake4 to run on breezy without a chroot.  I've written up some instructions here:

[http://skuld.bmsc.washington.edu/~yi/blog/?p=6]("http://skuld.bmsc.washington.edu/~yi/blog/?p=6")

Hope it helps some of you!

Yi

---

### Post by negatory on 2005-11-01
Works flawlessly!
You are a genious!
Now I just have to figure out how to get the sound working...any thoughts?I've tried with "+set s_device oss" but that did not work for me...
Thank you very much!

EDIT: A "quake4 +set s_driver oss +set s_numberOfSpeakers 2" fixed it!Thanks onde again!

---

### Post by Hg80 on 2005-11-01
ok goin try this tonight as i spent most of last nite trying to suit this problem out

---

### Post by dpw2atox on 2005-11-01
well i did all the steps and  its not working for me.

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory


thats the error i get.

---

### Post by rseymour on 2005-11-01
I must have a really screwed up system (or maybe it's the system's operator :???: )... your install looked so much easier than mine that I thought I'd give it a try to see if it would solve my "resolution" problem.

already had ia32 libs installed; had libSDL installed 2x (once in a nwn directory and once in my orig quake4 install).  followed your instructs to install libasound2 and libSDL-alsa in /emul/ia32-linux; did the ldconfig.  commented out my library path changes in the quake4 file and went back to the orig.  ran it and it ran w/o changing the desktop resolution ... unfortunately no sound.

changed out the alsa lib for the oss (since that's what I had working before with quake4) with the same result.

tried your instructions again w/o the libasound (and the oss version) and sure enough it worked.  now the only problem I have ... when I quit, the screen resolution in preferences shows 1280x1024 (which is what I want to run), but the actual resolution looks like it stays at 800x600.  So far the only way I've found to get my "normal" desktop back is to shutdown.  oh well ...

---

### Post by dmn_clown on 2005-11-03
[QUOTE=rseymour]tried your instructions again w/o the libasound (and the oss version) and sure enough it worked.  now the only problem I have ... when I quit, the screen resolution in preferences shows 1280x1024 (which is what I want to run), but the actual resolution looks like it stays at 800x600.  So far the only way I've found to get my "normal" desktop back is to shutdown.  oh well ...[/QUOTE]

The problem with OSS is that true surround sound does not work with it.  Alsa will work perfectly (at least on my system) just edit a few lines in the config file :

```
seta s_driver "alsa"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_pcm "surround51"
seta s_numberOfSpeakers "6"
```

no skips, no delays, no static.  Just pure surround strog exploding bliss.

I would assume that your resolution problem + solution lies within your /etc/X11/xorg.conf file.

---

### Post by yqiang on 2005-11-04
Hurmm interesting, if I set the driver to alsa, i don't get any error messages from the console but I do not have any sound, any clues?

---

### Post by dmn_clown on 2005-11-04
[QUOTE=yqiang]Hurmm interesting, if I set the driver to alsa, i don't get any error messages from the console but I do not have any sound, any clues?[/QUOTE]

Is libasound installed? ldconfig ran? Sound working elsewhere?

---

### Post by dolny on 2005-11-05
What port does Q4 use to connect to the server when checking the cdkey online?

---

