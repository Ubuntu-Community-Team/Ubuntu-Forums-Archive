---
title: "ALSA-sink Problems and Kaffine Problems"
date: 2006-05-08
forum: Desktop Environments
---

### Post by link141 on 2006-05-08
My journey with Linux is proving to be difficult, but I intend not to give up.

First off, I'd like to know if there is any major known problems with the ALSA driver because it's been causing me many headaches and much frustration.  The problem is that any application that attempts to use it always has problems.  With the majority of the sound apps, no sound comes out of the speakers  when they are transmitting a signal.  Most of the time, oblivious  to this fact.  That means  that they don't even send an error.  The OSS sound driver works perfectly without any problems.  I've had to change the default ALSA driver to the OSS sound driver in Amarok and switch to other OSS compatible programs.  KsCD doesn't work, as well as many others.  The fact that the default sound driver for all of the kubuntu sound problems isn't working disappoints me deeply.  If anyone has any experience or knowledge whatsoever that may aid in finding a solution to this annoyance, I would appreciate it greatly if those could step forth.  

The absolute most dedicated program to provide my daily frustration is kaffine multimedia player.  Whenever try to open a movie file, audio, or any other compatible media, it finds any possible error that it can use to deny it.  With audio it flashes through about three error windows and informs me that there is no useable audio driver on my system, at the same time as using an audio driver to torment me with the sound of breaking glass.  When trying to open a movie file, it goes vehemently ballistic, and piles six (that's right 6) error messages upon one another, informing me that my video driver doesn't work.  I have an intuitive yet questionable feeling that I'm not alone.  

Sorry if it seems as so I'm freaking out, but my computer seems as if some unseen force is using it to anger me :).  Again, if you know any way to aid me with my problems, please post your suggestions here.  If you need me to elaborate on any part of this, just ask.  Try to keep it though, simple I am still fairly new to Kubuntu :).  I greatly appreciate any help provided by this forum.  Thanks :).

---

### Post by Sef on 2006-05-08
Copy and paste these two commands to here:

1) cat /proc/asound/cards

2) sudo gedit /etc/modprobe.d/alsa-base

---

### Post by link141 on 2006-05-08
Although the first command worked, the second did not. Here is the error

sudo: gedit: command not found

By the way, Adept says that ALSA is installed, the base and COUNTLESS components.  I tried reinstalling it before, but it didn't work.  Sorry I did not say that.  Another problem my install is that many of the commands aren't recognized.  The Default shell under my username is /bin/bash .  Thanks.

---

### Post by RavenOfOdin on 2006-05-09
Use ESD instead of ALSA.

---

### Post by trotski on 2006-05-09
You may want to try arts as a driver instead of ALSA.  This is probably a software mixer issue.  ESD is more of a Gnome solution, so you may not want that -- not that arts will be around much longer.  Up to you.  BTW, Sef should have told you to do 

**kdesu kate** /etc/modprobe.d/alsa-base

Gedit is a Gnome tool.
He just wanted to see the output of both commands.

---

### Post by link141 on 2006-05-11
I've just installed Kubuntu Dapper Drake and EVERYTHING works!  I can get up to date versions of my favorite software, it's proven to be more stable, and many other of my problems are settled.  In my opinion, it's miles ahead of breezy.  Now I can see why so many others are using it as their current version.

---

