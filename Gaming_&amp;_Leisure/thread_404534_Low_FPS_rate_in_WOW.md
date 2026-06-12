---
title: "Low FPS rate in WOW"
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by ArtificialSynapse on 2007-04-08
I apologize to make another post like this, but I really can't seem to find any answers other then the standard. I'm trying to get WOW to run smoothly on my system, I've got a X2 2.2ghz AMD cpu running an integrated Geforce 6100 graphics card with 512 mb of RAM, 1.5 gb of system memory and 180hdd ( I forget the speed ), and the new Edgy release. Anyways, I've done all the normal tweaks, regedit, X server, tried some light weight desktop managers, and I really cannot get my fps above 10ish when I'm outside, and above 25ish in doors ( which is fine for me ). My opengl drivers are installed, the nvidia card is working properly, as the ut2k4 demo runs exceptionally well, looks well above 20fps. Does anyone know links to some different tweaks I might try, or just some ideas on here? Thanks for your help : )

---

### Post by hikaricore on 2007-04-08
What resolution are you running the game in (1024x768 works well)?
What colour depth is your desktop running in (personally I use 16bit to lower gpu strain)?

Have you turned down every video setting possible and disabled full screen glow effects in your testing?

---

### Post by ArtificialSynapse on 2007-04-08
Yup, every video setting is as low as it goes, and the res is at 800x600, I never thought about the color depth though, I'm going to go try that, although I wish I could run at 32bit, I imagine 16 will look ugly : \

Thanks for your imput so far, I'll get back to you in a few minutes!

---

### Post by ArtificialSynapse on 2007-04-08
Okay, now this is really weird, I open up WOW to attempt to change the settings and whenever I change the resolution and close out of it, it just goes back to how it was and doesn't make any attempt to change. Same thing with reverting back to 16bit color, but what was so weird, is when I clicked Defaults to return, and it boosted my settings up, my FPS actually raised about 10 points ( running around 20ish ), but then I turned my settings down and it went back to 8ish. Any way to change what the default settings are in the config.wtf or something like that?

---

### Post by ArtificialSynapse on 2007-04-08
Alright, I got both the resolution down, and the depth down, it still runs at the same crappy fps, what I've noticed is that when I have it in window mode, and the box is relatively small, the fps goes up, I'd like to run in full screen mode however, I'd be fine with just 20fps at this point.

---

### Post by konungursvia on 2007-04-08
What nvidia driver are you running?

---

### Post by ArtificialSynapse on 2007-04-08
The latest one from nvidia.com (1.0-9755) 

Basically the issue now is just that when the screen is maximized the FPS is low, when it's smaller, it's reasonable, like at half size, it runs at a smooth 25 ~ 30 fps outside, and 45 ~ 55 inside. When I'm maximized it's about 10 outside and 20 inside

---

### Post by rkryspin on 2007-04-08
they say no question's is stupid.  How do I measure fps.   Someone suggested glxgears.   Is there a log somewhere or a parameter to start glxgears with?   :confused:

---

### Post by justin whitaker on 2007-04-08
> **ArtificialSynapse said:**
> The latest one from nvidia.com (1.0-9755) 

Basically the issue now is just that when the screen is maximized the FPS is low, when it's smaller, it's reasonable, like at half size, it runs at a smooth 25 ~ 30 fps outside, and 45 ~ 55 inside. When I'm maximized it's about 10 outside and 20 inside

You already reduced the terrain distance, right? That's a killer. I dropped the draw distance a couple of notches, and went from 10-20FPS outdoors, to 30-40, which is more than playable.

Another things you might want to do is run in windowed mode. For some reason, WOW really responds well to running in windowed mode.

---

### Post by ArtificialSynapse on 2007-04-08
> **ArtificialSynapse said:**
> The latest one from nvidia.com (1.0-9755) 

Basically the issue now is just that when the screen is maximized the FPS is low, when it's smaller, it's reasonable, like at half size, it runs at a smooth 25 ~ 30 fps outside, and 45 ~ 55 inside. When I'm maximized it's about 10 outside and 20 inside

Yeah, everything is dropped, and windowed mode works okay, but I'd really like increased performance with at least an almost maximized screen. 

Somebody help please!

---

### Post by ArtificialSynapse on 2007-04-09
bump

---

### Post by lakersforce on 2007-04-09
It sounds like you might be running in D3D mode instead of OpenGL. D3D drasticly lowers framerate on older videocard models.

---

### Post by Sammi on 2007-04-09
Try adding these two lines to wtf/Config.wtf
```
SET ffxDeath "0"
SET ffxGlow "0"
```

---

### Post by ArtificialSynapse on 2007-04-09
I already addded those two lines, and I run wine WoW.exe -opengl , I guess my only issue is that it won't allow me to turn down the multisampling options, it constantly reverts back to 24bit. I have that addon installed that fixes those issues in opengl, and I can't even run in -d3d (crashes). Right now, if I run in windowed mode, liberally sized down outside it runs reasonable, and I can increase the screen size when I enter a building. That should I do?? thanks!

---

