---
title: "KWin and Fullscreen Flash"
date: 2011-05-03
forum: Desktop Environments
---

### Post by sffvba[e0rt on 2011-05-03
Hi all,

There seems to be a recurring theme with the KWin and full-screen flash causing it to crash (bug reports going back a long time attest to this).  I had to disable desktop effects in Kubuntu 11.04 to be able to watch Youtube clips full-screen and I do so miss the stunning visuals that KDE 4.6 brings.  

Anybody have more information on this, work around or anything so I can have desktop effects enabled and still view Flash movies?

Please note this is on my laptop using Intel graphics and it happens in FireFox 4 as well as Chromium (at least in Chromium I can restart KWin when it crashes, in FireFox I am left in the dark and need to restart :/)



Regards
404

---

### Post by kvv_1986 on 2011-05-05
SameHere (tm)

---

### Post by sffvba[e0rt on 2011-05-05
Switched to openSUSE 11.4 KDE... not having the same issue... so weird...


404

---

### Post by Wispero on 2011-05-12
I had the same problem, so I thought that It was something in the KDE 4.6.2, so I update to 4.6.3 but I had the same problem, so I removed something in (I dont know how it is called in english) system setting > desktop effect > advance and then suspend effect on desktop when fullscreen

[http://uppix.net/b/f/f/826d9a359feefac0d587006385d87.png](http://uppix.net/b/f/f/826d9a359feefac0d587006385d87.png)

well until now I don't have the Youtube's fullscreen problem
good luck ;P

---

### Post by bhandley on 2011-05-13
> system setting > desktop effect > advance and then suspend effect on desktop when fullscreen

The setting they are referring to is found in System Settings>Desktop Effects>Advanced. Uncheck "Suspend desktop effects for fullscreen windows."

Videos still act weird, but they don't crash KWin. When exiting fullscreen and returning to fullscreen, the video will maximize BEHIND the browser window. Minimizing the browser window seems to fix the problem.

---

### Post by Wispero on 2011-05-13
I had read about that problem in google, but I didn't have it, so I dunno about it but I remember that you have to change something in the behaviour of the windows

---

### Post by doomguard88 on 2011-05-25
> **bhandley said:**
> The setting they are referring to is found in System Settings>Desktop Effects>Advanced. Uncheck "Suspend desktop effects for fullscreen windows."

Videos still act weird, but they don't crash KWin. When exiting fullscreen and returning to fullscreen, the video will maximize BEHIND the browser window. Minimizing the browser window seems to fix the problem.

I had the same problem, where fullscreen flash was behind the browser. Couldn't fix so i switched to compiz with emerald and i can fulscreen anything now with no problems.

---

### Post by Zorael on 2011-05-30
> **bhandley said:**
> Videos still act weird, but they don't crash KWin. When exiting fullscreen and returning to fullscreen, the video will maximize BEHIND the browser window. Minimizing the browser window seems to fix the problem.

> **doomguard88 said:**
> I had the same problem, where fullscreen flash was behind the browser. Couldn't fix so i switched to compiz with emerald and i can fulscreen anything now with no problems.

See [this post](http://ubuntuforums.org/showthread.php?p=10880548) for a possible fix.

---

### Post by Wispero on 2011-06-18
> **bhandley said:**
> The setting they are referring to is found in System Settings>Desktop Effects>Advanced. Uncheck "Suspend desktop effects for fullscreen windows."

Videos still act weird, but they don't crash KWin. When exiting fullscreen and returning to fullscreen, the video will maximize BEHIND the browser window. Minimizing the browser window seems to fix the problem.

recently, I had the same problem with the fullscreen, you can fix it on** System Settings **then look for **WIndow Behavior** and then **"Focus strealing prevention level" **
then you have to select **"none"**.

I hope that It helps to someone  :P

---

### Post by 13east on 2011-06-20
I thought I had fixed this problem by suspending desktop effects for fullscreen apps but now whenever any flash video is put to fullscreen will crash the system.  All I get is complete black screen w/ no response from the machine at all... this problem started recuring after a recent system update... only thing that works now is suspending desktop effects completely or switching over to xrender.  Having these kind of problems where basic surfing is unusable defeats the purpose of having a flash desktop like kubuntu.

Has anyone found any sort of fix for this major glitch in Kubuntu?

---

### Post by geoaraujo on 2011-06-21
> **13east said:**
> I thought I had fixed this problem by suspending desktop effects for fullscreen apps but now whenever any flash video is put to fullscreen will crash the system.  All I get is complete black screen w/ no response from the machine at all... this problem started recuring after a recent system update... only thing that works now is suspending desktop effects completely or switching over to xrender.  Having these kind of problems where basic surfing is unusable defeats the purpose of having a flash desktop like kubuntu.

Has anyone found any sort of fix for this major glitch in Kubuntu?
This glitch was really annoying, but I managed to fix it just as you said: disabling deskop effects on fullscreen. KWin did not crashed since then.
Anyway, if flash is always crashing KWin on your Kubuntu, maybe you should try flash video replacer: [http://www.webgapps.org/add-ons/flashvideoreplacer](http://www.webgapps.org/add-ons/flashvideoreplacer)
It's just a guess, but who knows...

---

### Post by Wispero on 2011-06-21
> **13east said:**
> I thought I had fixed this problem by suspending desktop effects for fullscreen apps but now whenever any flash video is put to fullscreen will crash the system.  All I get is complete black screen w/ no response from the machine at all... this problem started recuring after a recent system update... only thing that works now is suspending desktop effects completely or switching over to xrender.  Having these kind of problems where basic surfing is unusable defeats the purpose of having a flash desktop like kubuntu.

Has anyone found any sort of fix for this major glitch in Kubuntu?

maybe is something with your video driver, better you can try with compiz instead of kwin

---

### Post by 13east on 2011-06-21
> **Wispero said:**
> maybe is something with your video driver, better you can try with compiz instead of kwin

how do i run compiz on kubuntu?

---

### Post by idoitprone on 2011-06-21
> **not found said:**
> Switched to openSUSE 11.4 KDE... not having the same issue... so weird...


404


that is because opensuse does a good job backporting patches compared understaffed ubuntu that flat out does not care as much

The screen flicker is a known issue of kde4 that is fixed in the later versions of kde. Some are because of driver others are because the full screen window behaviors Try to find a ppa or turn on compositing for full screen window - in think that fixes it with performance problems

---

### Post by Wispero on 2011-06-21
> **13east said:**
> how do i run compiz on kubuntu?

first you have to install compiz, and compiz fusion icon, then run compiz fusion icon and select Windows Manager -> Compiz

[http://wstaw.org/m/2011/06/22/pic5_.png](http://wstaw.org/m/2011/06/22/pic5_.png)

---

### Post by 13east on 2011-06-21
> **Wispero said:**
> first you have to install compiz, and compiz fusion icon, then run compiz fusion icon and select Windows Manager -> Compiz

[http://wstaw.org/m/2011/06/22/pic5_.png](http://wstaw.org/m/2011/06/22/pic5_.png)

tried it but seems compiz is just too wonky in performance... heavy lag time w/ respect to the screen responding to mouse inputs... a lot of screen distortions and taskbar kept getting misaligned... fullscreen flash vids work fine but they do well under xrender... and for me xrender is a lot smoother than compiz right now

---

### Post by Wispero on 2011-06-21
> **13east said:**
> tried it but seems compiz is just too wonky in performance... heavy lag time w/ respect to the screen responding to mouse inputs... a lot of screen distortions and taskbar kept getting misaligned... fullscreen flash vids work fine but they do well under xrender... and for me xrender is a lot smoother than compiz right now

I tried xrender, but if I watch some video on youtube, it gets too lag, If you use compiz. you lose some effects on blur or transparency, I prefer Kwin, but I don't know how to fix that in random times the screen start to blink, I thinking on go back to "unity" haha xd

---

### Post by 13east on 2011-06-21
> **Wispero said:**
> I tried xrender, but if I watch some video on youtube, it gets too lag, If you use compiz. you lose some effects on blur or transparency, I prefer Kwin, but I don't know how to fix that in random times the screen start to blink, I thinking on go back to "unity" haha xd

i've been running gnome for 5+ years and like how stable it is on most instances, if not a little bland out-of-the-box... i absolutely abhor unity and aesthetically i think it is absolute crap, although some of its functions are quite good so I hope they make their way across to the gnome shell... 

for me the only glitch that I cannot stand is the fact that the whole computer crashes whenever running fullscreen flash apps... others being "folder view layout" and "folder view plasmoid" cannot rename files w/out crashing the current desktop and cannot view "open with" options in right-click context menu, and the battery-indicator plasmoid displays incorrect percentage renaming after coming off sleep but will display correct time renaming (these glitches are minor compared to the fullscreen issue)... I have no other issue w/ Kubuntu 11.04 and it is very smooth visually and performance vise .. 

I've grown quite fond of the visual and functional aspects of kde and think I'll stick w/ it for a little while longer... 

hopefully an update comes around that can fix these issues soon 'cause until HTML5 is completely implemented across the web FLASH is of utmost importance and if simple fullscreen vid playback isn't stable running along side all of KDE's visual effects than it is pointless

---

### Post by Wispero on 2011-06-21
> **13east said:**
> i've been running gnome for 5+ years and like how stable it is on most instances, if not a little bland out-of-the-box... i absolutely abhor unity and aesthetically i think it is absolute crap, although some of its functions are quite good so I hope they make their way across to the gnome shell... 

for me the only glitch that I cannot stand is the fact that the whole computer crashes whenever running fullscreen flash apps... others being "folder view layout" and "folder view plasmoid" cannot rename files w/out crashing the current desktop and cannot view "open with" options in right-click context menu, and the battery-indicator plasmoid displays incorrect percentage renaming after coming off sleep but will display correct time renaming (these glitches are minor compared to the fullscreen issue)... I have no other issue w/ Kubuntu 11.04 and it is very smooth visually and performance vise .. 

I've grown quite fond of the visual and functional aspects of kde and think I'll stick w/ it for a little while longer... 

hopefully an update comes around that can fix these issues soon 'cause until HTML5 is completely implemented across the web FLASH is of utmost importance and if simple fullscreen vid playback isn't stable running along side all of KDE's visual effects than it is pointless

I like the effects of KDE because of that, I'm still on Kubuntu .. but well It has some bugs, I hope that you fix your problems with KDE :P

---

### Post by 13east on 2011-06-21
> **Wispero said:**
> I like the effects of KDE because of that, I'm still on Kubuntu .. but well It has some bugs, I hope that you fix your problems with KDE :P

thx... same goes for your issues w/ kubuntu

---

