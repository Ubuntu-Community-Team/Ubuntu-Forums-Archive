---
title: "Poor performance in native games (HB Psychonauts especially)"
date: 2012-09-14
forum: Gaming &amp; Leisure
---

### Post by Radwulf on 2012-09-14
I've been dual booting for a couple of years but have recently decided to try to get more games with native versions running in Ubuntu.  Some games such as Spacechem and World of Goo work fine but I'm getting serious frame-rate issues in higher requirement games such as Psychonauts (NB. all these versions are from Humble Bundle).

My laptop specs are:
i7 3610qm (i4000 integrated graphics)
GT 650m nvidia graphics
Ubuntu 12.04 tried with Unity and Gnome Shell (GS by default)
Bumblebee Bumblebee-nvidia 3.0.1-3-preciseppa1
Linux kernel 3.4.0-03040-generic (precise)
nvidia-current 304.43-0ubuntu1~precise~xup1 

I've installed the none USC versions to have greater control over install location and ease of modification such as using optirun.  My particular focus is Psychonauts with its very poor frame-rate.  Bastion runs OK but still seems sluggish.  Amnesia seems to run well although that could be the slow pacing from the little I played.  

I know very little about this as there seems to be so many areas that can go wrong (bumblebee performance overheads, drivers, WM compositing, etc).  I also don't know how to provide the necessary debugging logs.  I would greatly appreciate any help that is given.

Thanks for your time.

PS.  Does anyone know a reliable and easy way to see game frames per second?
PPS. I haven't tried any changes to WM compositing as I don't understand it, nor how I can change it in Gnome-shell.

---

### Post by pnarciso on 2012-09-14
Bastion and Psychonauts also run like crap compared to windows with my gtx680. 

They are bad ports, that's all.

---

### Post by Carborundum on 2012-09-15
> **pnarciso said:**
> Bastion and Psychonauts also run like crap compared to windows with my gtx680. 

They are bad ports, that's all.
Bastion runs pretty darn well on my laptop, which has integrated Intel graphics, so that's probably a problem on your end.

Psychonauts is a different story though...

---

### Post by bud986 on 2012-09-15
Baston ran well on my gaming laptop with GTX 460M, but wouldnt be to suprised if performance is a bit better on windows, due to nvidia drivers. I have heard that the new nvidia drivers are way better for the higher en cards on linux. 
[http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_win7_nvidia1&num=7]("http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_win7_nvidia1&num=7")

There also a bug in unity that might cause a slowdown, try playing using xfce or somthing else.

---

### Post by vexorian on 2012-09-15
Probability tells me this is caused by unity (actually compiz' fault).

So, try getting into the gnome fallback or unity-2d sesions and try again. If there is a noticeable performance gain, you can switch to these sesions when wanting to play these games and return to unity (Ubuntu) sesion when you are done. Or you can switch to one of those lower end desktop environments.

---

### Post by contributor on 2012-09-17
Bastion runs quite well on my system and I am fully satisfied with it's performance. My system specs is Intel® Core™2 Quad CPU Q6600 @ 2.40GHz × 4 ,3GB Ram, OCZ Petrol, 64GB SSD,AMD Radeon HD 5450,Ubuntu 12.04 with GNOME 3.4.1.

---

### Post by pnarciso on 2012-09-17
I play all my games with vsync, so the problem with Bastion is that it can't maintain a stable 60 fps, which the windows version do.

So, when it drops from 60fps I can feel the game stutter which is unacceptable to me. Others can tolerate this, but I don't.

---

### Post by Radwulf on 2012-09-19
Thanks for the responses.  I tried using xfce as my desktop environment as a bulletproof way of testing whether the problem was the window manager compositing (ie. compiz for unity and mutter for gnome-shell).  The result was immediate with games running at near Win7 levels of performance.  Torchlight and Bastion run fine and there were substantial gains in performance in Trine and SPAZ.  Psychonauts also dramatically improved but it is regrettably still insufficient with massive fps drops from about 60 to <10 in some areas.  According to Icculus Bug Tracker this is a known bug.

Although xfce makes playing games relatively convenient I would still prefer to play them in my desktop environment of choice, that is Gnome Shell.  The Window Manager is Mutter.  Does anyone know how I can go about disabling this for games?

---

### Post by pnarciso on 2012-09-19
Unfortunately you can't, because gnome 3 desktop is a plugin of mutter. The only way to run games without any composite is reverting to gnome fallback (no effects). 

Mutter supports unidirectional of full screen windows, but it only works in games that use sdl 1.2. If games use other sdl versions like 1.3 or 2.0  composite effects are not suspended.

Also, games that use mono or java won't work either.

---

### Post by vexorian on 2012-09-19
> **Radwulf said:**
> Thanks for the responses.  I tried using xfce as my desktop environment as a bulletproof way of testing whether the problem was the window manager compositing (ie. compiz for unity and mutter for gnome-shell).  The result was immediate with games running at near Win7 levels of performance.  Torchlight and Bastion run fine and there were substantial gains in performance in Trine and SPAZ.  Psychonauts also dramatically improved but it is regrettably still insufficient with massive fps drops from about 60 to <10 in some areas.  According to Icculus Bug Tracker this is a known bug.

Although xfce makes playing games relatively convenient I would still prefer to play them in my desktop environment of choice, that is Gnome Shell.  The Window Manager is Mutter.  Does anyone know how I can go about disabling this for games?
It is not written in stone that you cannot use 2 Desktop environments in the same computer. What you can do is simply log out from your Gnome 3 sesion and then select gnome fallback or XFCE before playing games (Since they are full screen games, it is no problem as you don't need other apps running anyway).

Anyway, for unity I do have a script that can switch it to unity-2D without killing the other applications. It might be possible in Gnome-3 to kill all the gnome 3 stuff and mutter and then run metacity and gnome-panel, but it migth be more complications than it is work.

Just as a test, close all your applications / save all work and try running this in the run dialog : metacity --replace , what happens?

---

### Post by Sealbhach on 2012-09-19
I always have Openbox installed and go into that when I want to play graphics intensive games.
.

---

### Post by vexorian on 2012-09-19
I exaggerate and use a desktop sesion  that *only* has a terminal :)

---

### Post by pnarciso on 2012-09-19
Also this issues could be avoided if all compositors had the option to shutdown themselfs when playing games at fullscreen, just like windows aero.

---

### Post by Sealbhach on 2012-09-19
Actually, I've been playing Torchlight without problems in KDE, there is an option in kwin to disable effects for fullscreen apps. Seems to work pretty well.

.

---

