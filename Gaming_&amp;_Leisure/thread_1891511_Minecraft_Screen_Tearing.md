---
title: "Minecraft Screen Tearing"
date: 2011-12-05
forum: Gaming &amp; Leisure
---

### Post by Nogueirn on 2011-12-05
Hey guys, I recently downloaded Minecraft for 11.10, and I was having some weird graphical issues. There seemed to be tearing and all the objects on screen would kind of change and look smaller. I then downloaded Sun Java 6 and tried running it with that, but then it wouldn't even boot up at all. Is there anything I'm doing wrong?

---

### Post by Nogueirn on 2011-12-05
bump... nobody?

---

### Post by overdrank on 2011-12-05
Hi and welcome, please be patient, it is polite to bump your thread once a day (24hr). Thanks :)

---

### Post by desktorp on 2011-12-06
Can you list your system specs and Minecraft's current video settings?

System settings you might look for might be: VSync / Sync to Vertical Blank or maybe Unredirect Fullscreen.  In Minecraft, the FPS Limit setting could be part of the problem; change from "Balanced" to "Max FPS"..

Are you launching from the terminal or by clicking on minecraft.jar?

---

### Post by Nogueirn on 2011-12-06
Processor: 4x Intel Core 13-2310M CPU 2.10GHz
Memory: 3967 MB
Oneiric Ocelot

I run Minecraft by opening it with Sun Java 6 so I right click it, but it doesnt open

---

### Post by Nogueirn on 2011-12-06
Also, my graphics card is 2nd Generation Core Processor Family Integrated Graphics Control

---

### Post by desktorp on 2011-12-06
I'm trying to stop myself from jumping to conclusions, but Intel graphics are notorious for crappy performance.  I can't say beyond a shadow of doubt that this is the case, here.. but I would be willing to bet that it's part of your problem.

The following page is outdated, but sheds some light on the problems people tend to have, when using systems with Intel GMA.  Just search for "GMA" on that page and see all of the reports of bad frame rates and unplayability, compared to all of the non Intel configurations that seem to run great.

[http://www.minecraftwiki.net/wiki/Hardware_performance](http://www.minecraftwiki.net/wiki/Hardware_performance)

Personally I hope this is not your problem, but it's not looking good for Intel graphics.

---

### Post by Nogueirn on 2011-12-06
[http://s1117.photobucket.com/albums/k591/Nogueirn/?action=view&current=Screenshotat2011-12-06094143.png](http://s1117.photobucket.com/albums/k591/Nogueirn/?action=view&current=Screenshotat2011-12-06094143.png)

There's a picture, and I couldnt capture it but the screen has massive tearing

---

### Post by Nogueirn on 2011-12-06
I couldnt find my exact laptop up there, my specs weren't together and were jumped around, but some said they run crappy, and others say they run great. I can tell you I don't have fps problems at all, its just the screen tearing and that weird stuff on the picture

---

### Post by ergo-proxy on 2011-12-06
Are you sure you have installed propietary java and in fact using it?

---

### Post by Nogueirn on 2011-12-06
How do I know if I am? Just to make sure

---

### Post by Nogueirn on 2011-12-06
How do I know if I am?

EDIT* sorry double post lol

---

### Post by Nogueirn on 2011-12-07
bump...

---

### Post by ergo-proxy on 2011-12-07
Just run those two commands in a termina:
> which java
> java -version

---

### Post by Nogueirn on 2011-12-07
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

thats what it said

---

### Post by bheussler on 2011-12-07
I am having the same problems as well.  Here is a screen shot: [http://i.imgur.com/Cm77u.png](http://i.imgur.com/Cm77u.png)

I literally have the same exact system specs.  I have a HP ProBook 4530s
Intel Core i3-2310M 2.1GHz
4GB DDR3
Intel HD Graphics 3000

I tried running both the OpenJRE and Sun JRE and saw no difference, though both could run Minecraft.  As stated above, every ran fine.  The game had no hiccups or slowdowns.  The only problem I am having is the screen tearing.

To provide a little more information, I installed Minecraft using a handy installed script: [http://www.filedropper.com/minecraftinstaller20](http://www.filedropper.com/minecraftinstaller20)
Though I am having graphics issues, this is a very good installer and more people should know about it.

---

### Post by Nogueirn on 2011-12-11
bump...

---

### Post by Nogueirn on 2011-12-12
bump

---

### Post by a2j on 2011-12-14
create a script in directory where your minecraft.jar file is
```
java -Xmx2048M -Xms2048M -cp minecraft.jar net.minecraft.LauncherFrame

```

make it executable and run it.

might help. if not, check graphic driver and update if necessary. if still no-go, I'd say issue is GPU.

---

