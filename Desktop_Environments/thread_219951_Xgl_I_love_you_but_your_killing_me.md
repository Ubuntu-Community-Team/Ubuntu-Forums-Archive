---
title: "Xgl I love you but your killing me"
date: 2006-07-20
forum: Desktop Environments
---

### Post by LiquidFlame on 2006-07-20
So after i installed Xgl everything seemed like it worked, but know i have no control over my mouse sensitivity and when i try to play videos in Mplayer and VLC and to full mode it's very choppy and slow.  I've searched the forum and i have not found an answer to either of my questions.  Any help would be great thanks.

---

### Post by jmhickman09 on 2006-07-20
It seems like you probably know a ton more about ubuntu than me, but I had similar problems and this worked for me:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure x. I had similar problems, and this just lets you set up the settings for your graphics card again. I think. The first part was to revert to the backup xorg.conf before I did this, because x didn't start at all.

Here's my post, hope it helps: [http://ubuntuforums.org/showthread.php?t=219055&page=1](http://ubuntuforums.org/showthread.php?t=219055&page=1) 
I got that stuff off of the second page. Basically my graphics card wasn't set up right, and this will let you reconfigure it. Now mine works perfectly.

---

### Post by jimmygoon on 2006-07-20
> **jmhickman09 said:**
> It seems like you probably know a ton more about ubuntu than me, but I had similar problems and this worked for me:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure x. I had similar problems, and this just lets you set up the settings for your graphics card again. I think. The first part was to revert to the backup xorg.conf before I did this, because x didn't start at all.

Here's my post, hope it helps: [http://ubuntuforums.org/showthread.php?t=219055&page=1](http://ubuntuforums.org/showthread.php?t=219055&page=1) 
I got that stuff off of the second page. Basically my graphics card wasn't set up right, and this will let you reconfigure it. Now mine works perfectly.

that sounds like it would probably toast his XGL settings (I could be 100% wrong here) but if I may ask to the original poster... how did you set up XGL? What graphics card do you have? May I recommend AIGLX?

---

### Post by John.Michael.Kane on 2006-07-20
AIGLX might be useful if your running ati hardware. if your on nvidia hardware then AIGLX is a no-go. doing sudo dpkg-reconfigure xserver-xorg could very well mess your current xgl setup, however. being that i never tried to do it on an xgl setup i can't be sure.

---

### Post by jmhickman09 on 2006-07-20
It just reconfigures it, I don't think it could make it any worse, only the same/better. Aren't you just changing the settings to better match your hardware?

---

