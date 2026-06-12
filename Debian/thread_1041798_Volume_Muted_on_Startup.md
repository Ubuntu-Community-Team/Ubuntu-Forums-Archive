---
title: "Volume Muted on Startup"
date: 2009-01-16
forum: Debian
---

### Post by icanfly0307 on 2009-01-16
Hi, Everytime I turn on my computer, every single audio channel is muted and I have to manually unmute it. This is really annoying as I primarily use this computer for browsing the internet and listening to music. Does anyone know what's going on and how I can fix it? Thanks for your suggestions...

---

### Post by ynnhoj on 2009-01-16
after you unmute that channels and have everything set as you'd like, you can use the [alsactl](http://alsa.opensrc.org/Alsactl) command to preserve those settings.  in a terminal..```
alsactl store
```..(might need a *sudo* before that command too)

and if you don't have the command, install the *alsa-tools* package.

---

### Post by MaindotC on 2009-01-16
Try the suggestion I posted on your other thread [http://ubuntuforums.org/showthread.php?t=1041799](http://ubuntuforums.org/showthread.php?t=1041799)

---

### Post by icanfly0307 on 2009-01-17
@ynnhoj: Thanks I'll try it once I get home.

@strAlan: I don't want to disable the startup sounds. I just need my volume settings preserved the way they are when I unmute them.

Thanks for your help. :)

---

### Post by MaindotC on 2009-01-17
The post I suggested is how to DISABLE them - you need to try the REVERSE of those directions.

---

### Post by ynnhoj on 2009-01-18
> **icanfly0307 said:**
> @strAlan: I don't want to disable the startup sounds. I just need my volume settings preserved the way they are when I unmute them.
yea, he's suggesting that you might have the sounds muted and as a result, your sound stays muted.  (seems to me that if that's what's happening, that would be a bug/glitch with Gnome/GDM though, wouldn't it..?  there's a big difference between 'mute startup sounds' and 'mute sounds altogether'! :D)

---

### Post by MaindotC on 2009-01-18
ynnhoj that's true but I'm just trying to follow a troubleshooting flow of eliminating that possibility.  I just want to make sure this isn't a simple thing like sound being muted instead of turning into this big complex issue of a driver putting the wrong value into a register or having to recompile the kernel with a different option or something along those lines.  If in fact it is a bug, then he should file a bug report.

---

