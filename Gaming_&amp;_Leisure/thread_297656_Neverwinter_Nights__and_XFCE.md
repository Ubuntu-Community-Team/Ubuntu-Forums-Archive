---
title: "Neverwinter Nights  and XFCE"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by Kashirigi on 2006-11-11
I'm having a weird problem with Neverwinter Nights and XFCE. Thanks to the howto on these forums, I've managed to get everything working -- movies and all.

It runs perfectly under Gnome. Unfortunately, I prefer XFCE, which is also set as my default session. It runs under XfCE, but there's a weird transparency problem where I can see the panels (faintly) under the game, and also the vestigial window labelled "Neverwinter Nights Client". The game is running full-screen (over top of the window), and nwn.ini has  "FullScreen=1"

On addition to that, I've done the "export XLIB_SKIP_ARGB_VISUALS=1" trick which generally solves most of the transparency problems (cf. rdesktop, frozen-bubble).

In case it matters, I am currently using an nVidia GeForce N6800, and Dapper, not Edgy.

Does anyone have any other suggestions? Thanks for your help.

---

### Post by shawn on 2006-11-11
Sounds very strange. I don't have a real fix for your problem but there is a way to start games on a new X server which would mean XFCE isn't in the background at all anymore. Take a look here:

[http://ubuntuforums.org/showthread.php?t=51486&](http://ubuntuforums.org/showthread.php?t=51486&)

It also means that you can switch between games and your desktop enviroment which is pretty handy.

---

### Post by leech on 2006-11-12
I'm going to hazard a guess that you're running Beryl or Compiz?  Generally before I go to play a 3D game, I switch off Beryl and use Metacity as my window manager.  

Leech

---

### Post by NESFreak on 2006-11-12
> **leech said:**
> I'm going to hazard a guess that you're running Beryl or Compiz?  Generally before I go to play a 3D game, I switch off Beryl and use Metacity as my window manager.  

Leech
agree.

I believe there is an option for beryl/emerald not to use effects on fullscreen apps. Don't know where to find it. Dumped beryl because of stability issues and tv-out.

NESFreak

---

### Post by Kashirigi on 2006-11-12
> **NESFreak said:**
> agree.

I believe there is an option for beryl/emerald not to use effects on fullscreen apps. Don't know where to find it. Dumped beryl because of stability issues and tv-out.

NESFreak

Actually, I'm not using beryl or compiz (although my xorg.conf is set up with  composite enabled.

However, now that I'm running in a separate xserver (thanks to xgame), my concern about this matter has dropped significantly.

Thanks for all your help. My gaming experience is much better now.

---

