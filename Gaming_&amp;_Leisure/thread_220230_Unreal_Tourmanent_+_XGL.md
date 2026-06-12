---
title: "Unreal Tourmanent + XGL ?"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by lzfy on 2006-07-21
Hi, is it possible to run ut classic while running XGL? I have the GOTY edition cd and the linux installer, just want to know if it is possible before I try to install it.

---

### Post by frodon on 2006-07-21
AFAIK, accelerated openGL apps don't work with Xgl.
If you want to play games use Xorg.

---

### Post by Perfect Storm on 2006-07-21
I've heard there's a tweak to do so. I can't remember it though, but how well it works and if it works as good as under Xorg I dunno.

---

### Post by frodon on 2006-07-21
Ha, i guess the tweaks you're talking about are to launch the game in a another xserver session, IMO it's more a hack than a tweak ;)
Xgame is a nice script for that, i made some tests at home and i lose 300 FPS over 1300 with my old computer so i would say there's a bit of power lost but that's worth it : 
[http://xgame.tlhiv.org/](http://xgame.tlhiv.org/)
If you can't reach the site the perl script is there : 
[http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2](http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2)

To make the script work, just tweak the ICEauthority file like that :
[http://ubuntuforums.org/showpost.php?p=781066&postcount=13](http://ubuntuforums.org/showpost.php?p=781066&postcount=13)

AI, maybe we could write a short UDSF guide for that, since it works pretty well.

---

### Post by Perfect Storm on 2006-07-21
Good idea. Though I won't touch XGL with an iron stick until it's stable and ready to use in public.

---

### Post by lzfy on 2006-07-21
> **Artificial Intelligence said:**
> Good idea. Though I won't touch XGL with an iron stick until it's stable and ready to use in public.

Well it works very stable with my ATI x700 :) 


@frodon  Thanks for that. maybe I'll try it. 

Is it possible to switch to another user whithout ending the current session, run the new session without XGl and then play the game?

---

### Post by frodon on 2006-07-21
Maybe it's possible, if it could help you i wrote a guide to switch between Xgl and xorg through GDM or KDM, it may fit you needs :
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

---

### Post by lzfy on 2006-07-21
> **frodon said:**
> Maybe it's possible, if it could help you i wrote a guide to switch between Xgl and xorg through GDM or KDM, it may fit you needs :
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

Thanks, but I already have it like that :)

EDIT:
Tried installing UT with the installer but it gives me this error
> lzfy@TURIONDAPPER:~$ sudo sh ut-install-436.run
Password:
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
lzfy@TURIONDAPPER:~$ sh ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
lzfy@TURIONDAPPER:~$


What am I doing wrong?

---

### Post by Thirsteh on 2006-07-21
> **frodon said:**
> AFAIK, accelerated openGL apps don't work with Xgl.
If you want to play games use Xorg.

In the XGL demo video from Novell, the author demonstrates XGL's features while playing Quake III: Arena.

---

### Post by lzfy on 2006-07-22
So none knows why I'm getting this error message? :(

---

