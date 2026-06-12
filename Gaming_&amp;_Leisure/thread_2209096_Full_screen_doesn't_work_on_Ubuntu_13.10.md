---
title: "Full screen doesn't work on Ubuntu 13.10"
date: 2014-03-03
forum: Gaming &amp; Leisure
---

### Post by kvikkjepwy on 2014-03-03
I tried doing Minecraft and TS2014 in full screen mode but whenever I do full screen mode and boot up a game in full screen mode, I can still see my desktop and all the apps on it, and I cant see my cursor. I have tried using Compiz Config, but it still doesn't work even after I restart the computer. I cant even play my games, leaving me to suffer, since they use full screen and I don't know how to fix it. Anyone know?

---

### Post by Jake_Paine on 2014-03-04
What version/flavor of Ubuntu are you using? What graphics drivers do you have installed?

Have you tried launching the game from the terminal if so can you see any output? I'm assuming that the games run fine in Windowed mode?

---

### Post by Mateusz Stachowski on 2014-03-04
You could also try installing compizconfig-settings-manager and enabling Legacy fullscreen support. Launch CCSM then go to Tools and then Workarounds and check that option. 

You may need to install compiz-plugins-extra to actually have Workarounds in CCSM.

If those things didn't help then there is a bug about fullscreen problems with games and Compiz.

[https://bugs.launchpad.net/compiz/+bug/734908](https://bugs.launchpad.net/compiz/+bug/734908)

---

### Post by kvikkjepwy on 2014-03-04
> **Jake_Paine said:**
> What version/flavor of Ubuntu are you using? What graphics drivers do you have installed?

Have you tried launching the game from the terminal if so can you see any output? I'm assuming that the games run fine in Windowed mode?
I'm using Ubuntu 13.10 amd64 and have an H81M motherboard from ASUS and Ubuntu is the only thing I can use until my dad gets me windows 7. I have a GeForce 9600gt graphics card and an Intel Pentium Processor with 3.20 GHz with 3.75 GB RAM with 149 GB of hard disk space.

Oh yeah, sure, the games run PERFECT in windowed mode but I don't know how to launch the game from the terminal/

---

### Post by Jake_Paine on 2014-03-05
If you change directory into the minecraft folder and run something like:

```
java -jar minecraft.jar
```

That should launch it. This post is quite interested and may be related to your topic or help you resolve your issues:

[http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client](http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client)

Is it the default nVidia drivers you have installed or have you installed the propitiatory ones from the nVidia website?

---

### Post by xREDEMPTIONx on 2014-03-05
I play Minecraft on 13.10 and Fullscreen definitely has issues but it is possible. Just keep hitting F11 and it will eventually go fullscreen. It often takes several tries for it to work and seems to work best when your actually in-game and not at the main menu. Also, when it does eventually go fullscreen sometimes the mouse will not rotate the camera the full 360degrees, just press ESC to go to the menu and ESC again to go back in-game and it will work again. I'm sorry I cant help with your other game.

---

### Post by kvikkjepwy on 2014-03-08
well, I have uninstalled ubuntu and installed windows 8... so i wont be using these forums for a while...

or i could use it in virualbox.

---

### Post by dannyboy79 on 2014-03-08
ah that sucks, i have no issues running MC in fullscreen mode but then again i have a GTX 760 and using the latest Nvidia driver from the website. AMD graphics cards and drivers are still very touchy in linux unfortunately but i did see recently the open source radeonsi driver is at about 80% of what the catalyst can do as far as performance.

---

### Post by xREDEMPTIONx on 2014-03-08
That's too bad :( I dual boot with windows 7 and Minecraft runs like butter in Ubuntu (solid 60fps). Windows hits 60 at times but tends to take big dips down to the 30's quite a bit, it drives me crazy. I don't know what it runs like on windows 8 though. I'll take the slight annoyance of hitting F11 a few times for a solid 60 anyday!

---

### Post by dannyboy79 on 2014-11-15
not sure if this helped or not because I am not certain that minecraft uses sdl but I added the following to my ~/.profile file (this was mostly so that Trine would launch on the correct monitor, it's my monitor that's located at +1920,0 since I have a dual monitor setup and my main gaming monitor is not the farthest left monitor)  now I can right click on the minecraft window and choose fullscreen and it properly makes the game fullscreen.  
```
export SDL_VIDEO_FULLSCREEN_HEAD=1
export SDL_VIDEO_FULLSCREEN_DISPLAY=1
```

---

