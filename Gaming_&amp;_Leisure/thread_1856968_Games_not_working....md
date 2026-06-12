---
title: "Games not working..."
date: 2011-10-09
forum: Gaming &amp; Leisure
---

### Post by Lauryxy on 2011-10-09
I just started using Ubuntu 11.04. This is the first time I use any Linux so I have spent a lot of time setting it up. Some time ago I installed 2 games: SABRE and Virus Killer. I downloaded them through the Ubuntu software center or whatever it is in English, Ubuntu somehow found out I am Estonian.
Anyways I can only run SABRE from root and through terminal and it skips all the menus and spawns me in the sky w/o letting me choose anything. I can't even find out what the controls are!
In Virus Killer it showed me the menus and when it was supposed to start playing it crashed. And after I installed the graphics card drivers it just gives me a message that the refresh rate is wrong and then I have to restart my computer.
BTW SABRE started working in root after I installed the drivers.
Why aren't these games working?

---

### Post by thatguruguy on 2011-10-09
It's difficult to diagnose your problems without more info.  What graphics card are you using?  What drivers do you have installed?  What messages are you getting when you try to launch these games from the terminal?

---

### Post by Lauryxy on 2011-10-10
I use NVIDIA GeForce 6100 nForce 405 graphics card and the driver I use is what the Ubuntu's driver installing tool(again sorry i don't know the English version) gave me. The name it gives is "NVIDIA graphics acceleration driver(current version) [Recommended]" NVIDIA X server settings gave me a driver version 270.41.06.
Also the driver installing thingy says that the driver isn't activated, any way to activate it?
Anyways Virus Killer gives me:
```
there is no soundcard
Sound 'sound/virusLaugh1.wav' not loaded
Sound 'sound/virusLaugh2.wav' not loaded
Sound 'sound/virusLaugh2.wav' not loaded
Sound 'sound/virusLaugh5.wav' not loaded
Sound 'sound/virusLaugh5.wav' not loaded
Sound 'sound/virusLaugh6.wav' not loaded
Sound 'sound/virusDestroyDir.wav' not loaded
Sound 'sound/virusKilled1.wav' not loaded
Sound 'sound/virusKilled2.wav' not loaded
Sound 'sound/virusKilled3.wav' not loaded
Sound 'sound/virusEatFile.wav' not loaded
Sound 'sound/dirDestroyed1.wav' not loaded
Sound 'sound/dirDestroyed2.wav' not loaded
Sound 'sound/dirDestroyed3.wav' not loaded
Sound 'sound/dirDestroyed4.wav' not loaded
Sound 'sound/dirDestroyed5.wav' not loaded
Sound 'sound/dirDestroyed6.wav' not loaded
Sound 'sound/fileDestroyed1.wav' not loaded
Sound 'sound/fileDestroyed2.wav' not loaded
Sound 'sound/fileDestroyed3.wav' not loaded
Sound 'sound/kernelBeam.wav' not loaded
Sound 'sound/powerup.wav' not loaded
Sound 'sound/clock.wav' not loaded
Sound 'sound/explosion.wav' not loaded
Sound 'sound/gameOver.wav' not loaded
Made 10,000 unsuccessful attempts to grab 4 inactives directories!!
```Probably means I have to find drivers for my sound card but I haven't found one. I have Realtek High Definition Audio if I remember correctly.
And SABRE gives:
```
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
svgalib: Failed to initialize mouse.
Sabre Fighter Plane Simulator Version 0.2.4b 11/21/99
Initing graphics
Initing graphic interface
svgalib: can't open /dev/tty0 

```That is under normal user. Under root totally different things are happening (which I described in the first post).
I hope that is enough information :) If there are any more places I can get information about this please let me know. 270.41.06.

---

### Post by thatguruguy on 2011-10-10
A quick look at the Ubuntu Software Center listing for SABRE shows that there are a lot of comments indicating it isn't working.  Apparently, there hasn't been any development on it for some time.  That one may be a lost cause.

---

### Post by Lauryxy on 2011-10-10
What about Virus Killer? It can't be a sound card problem, LBreakout 2 which I just installed seems to work fine(except for some lag)and it does play sounds. Has it dropped out of development too? Can't check right now because I am away from MY computer right now and this one doesn't have any Linux distros on it.

---

### Post by thatguruguy on 2011-10-10
According to the Software Center, you're not the only one having issues with sound in Virus Killer.  You may consider filing a bug report about either or both of the games.

---

### Post by Lauryxy on 2011-10-13
well, guess i gotta check the comments before i dl something... I thought they only show stuff that works there... Thanks for your help anyway!

---

