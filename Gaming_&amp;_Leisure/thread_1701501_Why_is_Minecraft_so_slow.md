---
title: "Why is Minecraft so slow?"
date: 2011-03-06
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2011-03-06
I removed OpenJDK and installed Sun Java, but still, I'm getting a lot of problems. The app itself launches fast, but when I log in, I see the Mojang (developer) logo for at least 1-2 minutes. Then, I'm able to launch a world. When I'm playing, there's substantial lag. My specs are high-end, too.

What should I do?

---

### Post by mmsmc on 2011-03-06
please post your specs

---

### Post by Cam! on 2011-03-06
It mostly has to do with your Java + CPU.

CPU: Intel Q6600 (Quad Core, 2.4GHz)
RAM: 4GB
GFX:  ATI Radeon HD 4850 (Although no proprietary drivers are in use. I'm using 11.04 Alpha 3.

---

### Post by keltic dave on 2011-03-06
Can I ask why people have such problems with openJDK. I run minecraft just fine with it no slow down or anything infact I find the stability much better than my experience using minecraft on windows. 

Anyway you shouldn't be getting any problems at all unless you're running it on 64bit OS distro.

---

### Post by Cam! on 2011-03-06
I'm running it on 32-bit 11.04 Alpha 3. Even on 10.10 it was laggy.

---

### Post by keltic dave on 2011-03-06
> **Cam! said:**
> I'm running it on 32-bit 11.04 Alpha 3. Even on 10.10 it was laggy.

this might be a shot in the dark but it could be ATI. I use Nvidia as driver support for that seems far better.

---

### Post by Cam! on 2011-03-06
On Windows, my ATI card works fantastic.

---

### Post by Nutbun on 2011-03-06
I run it on 64 bit Ubuntu and a ATI card, and it runs great.
Maybe you haven't installed the additional graphics drivers.

---

### Post by keltic dave on 2011-03-06
try doing this then

go to the folder you have the minecraft.jar in create an empty file name it run.sh then copy this code into it.

```
java -Xms512M -Xmx1024M -jar Minecraft.jar
```

---

### Post by Cam! on 2011-03-06
> **Nutbun said:**
> I run it on 64 bit and a ATI card, and it runs great.
Maybe you haven't installed the proprietary ATI drivers.

Every time I install the proprietary ATI drivers, it renders Ubuntu useless. I can't get to the log-in screen without a graphical glitch or the monitor turning off.

Also, what folder do I put it in? The folder that has my Minecraft shortcut, or the Minecraft folder with all its data?

---

### Post by keltic dave on 2011-03-06
the place were you have the minecraft.jar downloaded too. But from reading what you've typed it sounds to me that it's definitely something up with ATI. or could be the fact you're using a alpha release of ubuntu. Maybe drive downgrading to 10.10 again and try the additional drivers again ?.

---

### Post by Veikk0 on 2011-03-08
Most likely it's a bug in Minecraft itself since other people are having the same problem too ([http://www.minecraftforum.net/viewtopic.php?f=1020&t=192754&start=30#p2791853]("http://www.minecraftforum.net/viewtopic.php?f=1020&t=192754&start=30#p2791853")). I've also experienced significant slowdown, but only with multiplayer. It worked just fine for me before the 1.3 update, now I only get under 10 FPS. I've no performance regressions in single player, though.

I guess we'll just have to wait for Mojang to fix it...

---

### Post by jerodev on 2011-03-08
Minecraft used to be slow for me too, but i doubbled the amount of ram and now it works fine. ;)

```
java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame
```

---

### Post by Riskexas on 2011-03-09
gosh my PC is way slower and it doesn´t lag at all i´m just using this:

cd <location of minecraft>
java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

BTW u have to wait 1 min in game so lag go away it works for me ;)

---

### Post by donkyhotay on 2011-03-09
> **Cam! said:**
> Every time I install the proprietary ATI drivers, it renders Ubuntu useless. I can't get to the log-in screen without a graphical glitch or the monitor turning off.

I've heard rumors that ATI is getting better but I have always been dissapointed with ATI driver support on linux. The FOSS drivers don't do the 3D acceleration right and the proprietary drivers are a pain to get working (but do pretty good once you get them working). I originally had an ATI card on my old system with ubuntu and hated it enough that when it was time for me to get a new system I made certain it had an nvidia card.

---

### Post by Nutbun on 2011-03-09
It must be certain models because my ATI 5850HD works like a dream with the  proprietary drivers.

---

### Post by LafTur on 2011-06-08
Greetings community!  :D  Currently, Minecraft 1.6 is out.

Toshiba Satellite
Ubuntu 11.4
4GB RAM
Dual core AMD
ATI Mobility Radeon 4200 series set.

Even after the installation of the ATI proprietary drivers the game runs at a low framerate.

I tried running the scripts you people listed, but none seemed to have any effect.
This game runs great on Windows 7... same computer.  Let me get this straight: No one has had any problems with NVidia?
Could this be connected to the frequent Flash Player problem I keep hearing about?
Also, I hear that downgrading to Ubuntu 10.10 solves some of these issues... would anyone care to confirm so that I don't switch only to be disappointed?

---

### Post by desktorp on 2011-06-08
Have you tried going to options > video settings and changing "performance" from *balanced* to *Max FPS*..?

---

### Post by John_Anon on 2011-06-08
Not a real technical answer, but what always helps is tweaking the settings. Such as:
Tiny distance rendering
Fast graphics
Small GUI 

...And avoid Creepers. ;)

---

### Post by ojdon on 2011-06-08
Minecraft needs 3D acceleration, you'll only be getting 1-3FPS without it.

Does your driver support 3D Acceleration?

---

### Post by h4ck3r on 2011-06-17
IF your minecraft is slow, first, make sure you have this installed:

```
sudo apt-get install fglrx-modaliases
```

Then, using Jockey install the proprietary drivers. (you can start jockey from the terminal with the command: "jockey-gtk")

Next, try and run aticonfig --initial, not sure if you'll be able to do this or not.

Finally, following this blog post, add this to your Device section in your xorg.conf:

[http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

```
Section "Device"
 Identifier "ATI Radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection
```

Simply put, the goal of this is to first, install the proprietary ati drivers, then add those lines of code to your "/etc/X11/xorg.conf" file's device section. You may need to create one if there already isn't one there. I'll try and help anyone, if you don't understand my instructions, or get stuck in the process. This was hurriedly thrown together and isn't a really complete guide on how to install the proprietary drivers.

My xorg.conf file looks like this:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
                Virtual 5760 1200
        EndSubSection
EndSection

Section "Module"
        Load  "extmod"
        Load  "dbe"
        Load  "xtrap"
        Load  "record"
        Load  "dri"
        Load  "glx"
        Load  "GLcore"
        Load  "freetype"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "DRI"
       Mode 0666
EndSection
```

---

### Post by holastickboy on 2011-06-23
I second that, you definitely need hardware 3d rendering, and without driver support, it's simply not going to happen.  With your specs, I have no doubt that the problem is the fact it's a driver issue.

---

### Post by Bdiah on 2011-10-15
Prefaced: I am using a ATI Radeon HD Mobility 4500 series

With the open source drivers I have been having the same low framerate issue.

Unfortunately, when I have attempted the solution of installing the proprietary drivers and editing the xorg.conf file, minecraft simply crashes when rendering the world.  I've seen several other threads with the same issue, but no solution other than switching back to the open source drivers (which is the source of the initial problem).  Any ideas or are we at the point where we just wait for the problem to be resolved in the drivers?

---

### Post by twinkies on 2012-11-17
minecraft is so laggy i tried everything but nothing works :(:(:(

---

