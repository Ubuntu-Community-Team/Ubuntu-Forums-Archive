---
title: "Xine Playback Help"
date: 2006-05-24
forum: Desktop Environments
---

### Post by MJ50 on 2006-05-24
I'm currently running Xine 0.99.xx trying to play avi file which is MPEG-4.
If I just start xine program, i get "There is no mrl" message on top.
If I double-click on the AVI file, it's playing but the screen is blank (black).
If I double-click the AVI file again, another xine window comes up and that ones displays the video perfectly.
I've tried on other system but that one works fine.
Any ideas?

---

### Post by an.echte.trilingue on 2006-05-24
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by ispmarin on 2006-05-24
What is the error in the "no mrl"?

---

### Post by MJ50 on 2006-05-25
Como vai Ivan?
I don't get any error message.
It plays the file but the screen is black.
If I move any window over the screen, then I see the video.

---

### Post by ispmarin on 2006-05-25
Tudo bem! E com você?
What is the driver that xine is using? Some options are xv, x11. Sometimes the mplayer does this kind of problem, don't know if the same happens to the xine...
Besides, what is the graphics card driver that you are using?
Did you try to play the same movie on totem, mplayer?

---

### Post by MJ50 on 2006-05-25
I've tried both xine and totem.  They have same results.
I'm using ATI Radeon 9200.
How do I check what driver xine/totem is using?

---

### Post by an.echte.trilingue on 2006-05-26
Totem and xine are the same thing (well, totem is another front end for libxine).

Xine attempts to use hardware acceleration by default, it could be that your video card is not set up right.  You could try 

```
sudo dpkg-reconfigure xserver-xorg
```

to make sure that everything is set up right, but probably that is not it.  

I do not know how to check xine settings from totem, however if you install Kaffeine and kaffeine-xine (also just another front end for libxine), you can mess with xine's settings under settings--->xine engine parameters --> video.

You installed all the necessary codecs like libxvidcore4 and ffmpeg, right?

---

