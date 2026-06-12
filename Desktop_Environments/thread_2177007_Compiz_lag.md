---
title: "Compiz lag"
date: 2013-09-26
forum: Desktop Environments
---

### Post by ruddi on 2013-09-26
For some reason when I drag the windows around it lags, I have searched high and low all around the Internet for a solution but I cant find anything that works for me.
I have tried to configure some settings in compiz with little luck but its better now then when I had the default settings but it is still laggy
I tried to disable Detect Refresh Rate and set the refresh rate at 120(the monitor is 60) I disabled vsync in the nvidia settings but it is on in compiz, if it is not on in compiz i get crazy screen tearing
So i was wondering if there is anything that I can do to make it better

System specs
intel i7 3770K @4.5
16gb ram
geforce gtx 760 with 325.15 driver (I have tried different drivers with no luck)

Thanks in advance :)

---

### Post by stinkeye on 2013-09-26
Ubuntu release?

---

### Post by ruddi on 2013-09-26
oh yeah sorry about that, 13.04 :)

---

### Post by stinkeye on 2013-09-26
Compiz runs fine here using nvidia or nouveau drivers.
Using 13.04.
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 313.30

Does the lag also occur in the guest session?

---

### Post by ruddi on 2013-09-26
Its much better in the guest session, there is absolutely no lagg at all, but when dragging a window I cant read what is inside the window even if the text is large, its kind off hard to explain, there is no lagg but it is still not as smooth as when I am running windows

---

### Post by stinkeye on 2013-09-26
Is this an upgrade or fresh install?

If it's better in the guest session may want to set compiz back to default.
In terminal...
```
dconf reset -f /org/compiz/
```

Log out/in.

---

### Post by ruddi on 2013-09-26
It is a fresh install
It's better, there is no lag but it is stil choppy(?) :(
Im sorry english is not my native language and i am not really sure how to describe it I hope you know what I mean :)

---

### Post by stinkeye on 2013-09-26
If your video card is compatible you would have been running the open source nouveau drivers
when you first installed ubuntu.
Did you experience problems before installing the nvidia driver?

What's your output from this command....
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by ruddi on 2013-09-26
It was fine before I installed the drivers

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 760/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.15

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by stinkeye on 2013-09-26
> **ruddi said:**
> It was fine before I installed the drivers

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 760/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.15

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Ok I am not a driver expert but if your not running any 3d games the nouveau driver is fine for normal
desktop use.
I am only using nvidia drivers at the moment because I am looking at some steam games.
May want to revert to the nouveau driver.

---

### Post by ruddi on 2013-09-26
I got the proprietary drivers so I can play Dota 2 
And ofcourse thank you for your time :)

---

### Post by ruddi on 2013-09-26
I got the proprietary driver so I can play Dota 2, is there maybe some settings within nvidia x server settings I should try or compiz? 
But anyway thank you for your time :)
(the other post didnt show then it magically appeared)

---

### Post by stinkeye on 2013-09-26
> **ruddi said:**
> I got the proprietary drivers so I can play Dota 2 
And ofcourse thank you for your time :)
I came across this in a post....
>  Note that the GTX 760 needs nvidia driver >= 319.32, and this is not found in the raring/13.04 repos. 

For someone else to help may want to explain how you installed the  NVIDIA 325.15 driver.

Driver may just be buggy in compiz.
Test in another environment like gnome-fallback perhaps.

---

### Post by ruddi on 2013-09-27
hmm, I followed this tutorial [http://www.youtube.com/watch?v=FPb9hfKUOFY](http://www.youtube.com/watch?v=FPb9hfKUOFY) and chose the "newest" drivers on [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa).
But on the nvidia website it says that 319.49 is the newest driver, will try 319.49 and see if it gets better.

---

### Post by ruddi on 2013-09-27
I installed the 319 driver with no luck.. but i noticed when I had the nouveau drivers enabled after uninstalling the 325 driver everything was smooth as butter.
If anyone has a suggestion to what I can do it would be greatly appreciated :)

---

### Post by ruddi on 2013-09-27
So I read in a post that unticking framebuffer object and vertex buffer object might make it smoother, and what do you know it actually is smoother. Not as smooth as with the open source drivers but much much smoother. So my question is, what does unticking them mean? :)

---

### Post by stinkeye on 2013-09-29
FYI I installed the 325.15 drivers and updated packages from the xorg-edgers ppa
and runs fine here with my gfx.
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.15

---

### Post by mc4man on 2013-09-29
> **ruddi said:**
> I installed the 319 driver with no luck.. but i noticed when I had the nouveau drivers enabled after uninstalling the 325 driver everything was smooth as butter.
If anyone has a suggestion to what I can do it would be greatly appreciated :)

Not sure if this applies to you but anyway - 
One big diff between nouveau & prop drivers is with cards that use 'powermizer.'  With nouveau you are always at the highest clock speed, with the prop drivers it is scaling the clock speed as needed. 
Many compiz 'actions' need a higher speed but there can be a short lag between needing it & getting it

So if your card uses powermizer try setting to max performance & see if the lag goes away.

---

### Post by ruddi on 2013-09-29
I always have it on max performance, but thanks anyway :)

---

### Post by ruddi on 2013-10-03
So, I tried to reinstall the system but nothing changed..
This is really ruining my Ubuntu experience so if anyone has any suggestions they are greatly appreciated.

---

### Post by ruddi on 2013-10-07
I fixed my problem.
I enabled Force synchronization between X and GLX in Compiz -> Workarounds.

(Edit)
OK
So for people with the same problem as me do NOT enable Force synchronization, instead follow these instructions [http://www.nvnews.net/vbulletin/showthread.php?t=110854](http://www.nvnews.net/vbulletin/showthread.php?t=110854)
I know the thread is from 2008 but hey, it actually worked for me.

---

