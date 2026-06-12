---
title: "Breathing between clicks; Misc. Issues"
date: 2005-01-08
forum: Desktop Environments
---

### Post by jakeslife on 2005-01-08
I have been using Ubuntu exclusively for weeks now, but I am running into one small (small to some, huge to others) issue: The click-to-click speed seems a bit slow. 

When I click on Applications it takes a breath, then when I mouseover Multimedia (or any other menu) it seems like it's lagging. I'm using Gnome right now, and haven't had a chance to really try any other WM's yet. I like Gnome, but I've never experienced it this slow on my machine (2 GHz, 1GB RAM). Even Mandrake or SuSE Gnome is a bit faster. 

Some other small issues I'm having are:

*Playing WMV files in any media player. I've read the HOWTO's, and I can play RM, AVI, RA, MOV, MP4...pretty much everything but WMV. But in icon view it has the screenshot of the video file it just says it doesn't have the right codecs to play it.

*I have Firefox 1.0 set as my default browser. When I installed Ubuntu I dumped .9RC and installed 1.0. In Thunderbird, or any link outside of Firefox, it doesn't open Firefox as the default browser. In fact, it doesn't open any browser. I know it's just a simple ctrl+c, but I shouldn't have to do that.

*Gaim is not connecting to my MSN screen name. Also, (correct me if I'm wrong, because I would love to be) no messenger for linux has Yahoo Webcam support.

*~not Ubuntu specific~ I'm going to be getting rid of my two NTFS partitions (as son as I figure out how I'm going ot back up 80 GB of data) and installing Ubuntu as my primary OS, but will still keep a Windows install for emergency reasons. I have an 80 GB HD, long with several smaller drives. Ideally I would love to have two seperate HD's (one with Ubuntu, one with XP Pro) but I don't have enough power connectors in my case. Is there such thing as a power splitter for these cables? If so, I haven't been able to find any.....

---

### Post by Darrena on 2005-01-09
> *Playing WMV files in any media player. I've read the HOWTO's, and I can play RM, AVI, RA, MOV, MP4...pretty much everything but WMV. But in icon view it has the screenshot of the video file it just says it doesn't have the right codecs to play it.


Are you using Totem or Mplayer?

> 
*I have Firefox 1.0 set as my default browser. When I installed Ubuntu I dumped .9RC and installed 1.0. In Thunderbird, or any link outside of Firefox, it doesn't open Firefox as the default browser. In fact, it doesn't open any browser. I know it's just a simple ctrl+c, but I shouldn't have to do that.

Set the path to firefox under preferred apps for example:
usr/lib/mozilla-firefox/firefox "%s"

> *~not Ubuntu specific~ I'm going to be getting rid of my two NTFS partitions (as son as I figure out how I'm going ot back up 80 GB of data) and installing Ubuntu as my primary OS, but will still keep a Windows install for emergency reasons. I have an 80 GB HD, long with several smaller drives. Ideally I would love to have two seperate HD's (one with Ubuntu, one with XP Pro) but I don't have enough power connectors in my case. Is there such thing as a power splitter for these cables? If so, I haven't been able to find any.....



You can pick up a power splitter for under $5 at any computer shop or maybe even Radio Shack.

---

### Post by jakeslife on 2005-01-09
I have tried both Totem and MPlayer. I have the wmv libraries installed but they still don't work for some reason.

I got the default browser thing fixed.

---

### Post by Darrena on 2005-01-09
[QUOTE=jakeslife]I have tried both Totem and MPlayer. I have the wmv libraries installed but they still don't work for some reason.

I got the default browser thing fixed.[/QUOTE]
 Run totem from the console and try opening a WMV file and see what it tells you

---

### Post by jakeslife on 2005-01-09
It will open the file, but the file ends up being a bit choppy and with no sound. I also can't play WMA files.

---

### Post by Darrena on 2005-01-09
[QUOTE=jakeslife]It will open the file, but the file ends up being a bit choppy and with no sound. I also can't play WMA files.[/QUOTE]
 How did you install your codecs?

---

### Post by jakeslife on 2005-01-09
sudo apt-get install bleh!

---

### Post by fng on 2005-01-09
try the package 'w32codecs' for a change :)

---

### Post by jakeslife on 2005-01-09
:-P I did do that. Still no work.

---

### Post by Darrena on 2005-01-09
[QUOTE=jakeslife]:-P I did do that. Still no work.[/QUOTE]
 What video card are you running and verify that you are not using the default VESA driver, or maybe try using the default VESA driver  ;)

---

### Post by maxim_86ualb2 on 2005-01-10
you can find a power spliters @ Pc shops everywere..as someone has stated... and you can make one from parts of another Power cable.... just cut it off....and duct tape the wires to ur working system (make sure it is not runing :P ) and be sure to follow the collor code.... & you will have ur self a new power connector.... but make sure that us case can handel the load...

---

