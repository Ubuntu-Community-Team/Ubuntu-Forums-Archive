---
title: "Tweak cs source to run like windows good fps?"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by jinxy1919 on 2007-01-10
Hey does anyone have a nice simple broken down guide on how to install source so that you can play it and get good frames like on windows?

---

### Post by kombucha on 2007-01-10
I actually just installed Cedega into Edgy and the first thing I installed was Steam. I literally just tested CS:S, and it worked wonderfully. I used this site as a guide for settings: [http://www.oddprocess.org/wp/2006/11/30/counter-strike-source-cedega-settings/](http://www.oddprocess.org/wp/2006/11/30/counter-strike-source-cedega-settings/)

I don't have great hardware to begin with, so my framerate isn't anything to write home about (20 FPS on the Video Stress Test with moderate settings on a Radeon 9000, Athlon XP 2000+, 512 MB RAM) but I'm sure you'll see much better results. Crossover Linux 6 was released yesterday with new support for Steam games, but I haven't tried it out yet, and now I really don't see the need to.

Make sure you have your graphics card drivers installed and 3D working properly first...

---

### Post by jinxy1919 on 2007-01-10
Is cedega better than wine and were can i get cedge for free or is it gonna cost me?

---

### Post by jinxy1919 on 2007-01-10
Ok i have purchased cedga wich one i download for dapper 6.06 ubuntu and install

---

### Post by kombucha on 2007-01-11
Um... download the newest version that is a .deb if possible? I don't know how their site works for registering and all.

I can only assume it's better in some ways because it is a commercial product (eww, that's an awful statement, but likely true in this case). I think it's better for games, whereas Wine (and Crossover Linux) is probably better for apps, although any of them can likely do both.

It's probably worth testing on your own system.

---

### Post by jinxy1919 on 2007-01-11
Well with wine im haven weird issues with css im fixen to try this and see how it goes if i need help ill make a post

---

### Post by kombucha on 2007-01-11
Well, if you already purchased Cedega, and we know that the settings in the link above make it run perfectly... maybe it'd be easier to just go there? I don't know about Wine, but with Cedega you won't even need to install it again...

---

### Post by jinxy1919 on 2007-01-11
Well um updating source now and it auto insalled everything i needed i like it so far and it even auto puts in in the right folder but the cedgea test said my 3d acceleration failed how i fix that everything shows right the new drivers do i have to turn 3d acceleartion on if so how?

---

### Post by jinxy1919 on 2007-01-11
> **jinxy1919 said:**
> Well um updating source now and it auto insalled everything i needed i like it so far and it even auto puts in in the right folder but the cedgea test said my 3d acceleration failed how i fix that everything shows right the new drivers do i have to turn 3d acceleartion on if so how?

Forgot to mention with wine with alot of things missing like the mozzila pugs and stuff i got like 30-60 fps and the funny thing is 3d accelertation isnt worken and on glxgears -printfps i get like in the 180-200 on an x850 pro werid? but anyway how you fix 3d acceleration

---

### Post by kombucha on 2007-01-11
Well... if glxgears works, then 3D acceleration is working... that's the tester. You see the cogs and all?

What test specifically did Cedega fail on?

And what are you using for drivers?

Try this in terminal: glxinfo
and also this: $ glxinfo |grep vendor

I don't really know enough to analyze the results, but those both deal with 3D card drivers and whatnot.

I just know I'm using AIGLX, vs. FGLRX and XGL I believe...

---

### Post by maxamillion on 2007-01-11
You will never get the performance out of a Windows game run on Linux, there is an emulator required and will always slow things down. Cedega should give you better fps then wine did, but it won't be as good as on Windows. This isn't a fault of Linux, its a simple matter of running code natively and running it on an emulator.

---

### Post by jinxy1919 on 2007-01-11
xo@xo-desktop:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.
xo@xo-desktop:~$

---

### Post by kombucha on 2007-01-12
Uh... looks good, maybe? I don't know...
Try "glxinfo |grep direct". I know that's important, too.

But aren't Cedega and Wine more than emulators in that they use the API sort of natively? I really don't know how they work, but I thought the difference between them and virtualization like VMWare and Win4Lin was that they use your hardware fully...

---

### Post by Fitzy_oz on 2007-01-17
> **jinxy1919 said:**
> xo@xo-desktop:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.
xo@xo-desktop:~$

Your looking for a line that says direct rendering: yes or direct rendering: no.  If it says no, your going to get horrid performance out of it.  That being said, once you have direct rendering working, the performance is going to be more than reasonable given that it is running under a compatibility layer which is far better than running it under bochs or vmware.  I find in CS:S over 25fps is playable anything over 35fps and I can't tell the difference anyway.  (It's probably why I suck at it though :))

Make sure the fglrx kernel module is running and that X-Windows is using the fglrx driver opposed to the "ati" or "radeon" DRI drivers.   Also try the latest driver from ATI's repo, this upped performance a little bit.  There is a great guide on how to install these drivers [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

There are also quite a lot of switches with wine that you can use to speed it up:
try running steam from the terminal with the following options:
# WINEDEBUG="-all" wine "c:\Program Files\Valve\Steam\steam.exe".
More information on this is in the [CS:S Edgy Thread]("http://ubuntuforums.org/showthread.php?t=304528&page=6&highlight=counter-strike+source")

Give that a try.

---

