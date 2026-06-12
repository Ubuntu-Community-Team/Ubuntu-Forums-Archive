---
title: "Minecraft not launching... Unable to edit .jar properties..."
date: 2013-04-19
forum: Gaming &amp; Leisure
---

### Post by soloman469 on 2013-04-19
Now i've had enough trouble with TF2. Now i'm having trouble trying to edit the permissions to even LAUNCH Minecraft. Somebody please help this is really starting to tick me off...

[COLOR=#000000]My computer specs:[/COLOR]
[COLOR=#000000]-Ubuntu 12.04 (precise)[/COLOR]
[COLOR=#000000]-Intel(R) Pentium(R) D CPU 3.40GHz[/COLOR]
[COLOR=#000000]-Frequency:3389.176 MHz[/COLOR]
[COLOR=#000000]-L2 Cache:2048 KB[/COLOR]
[COLOR=#000000]-Memory Total:3000 MiB

I got this computer for free from a place called Free Geek if that helps.[/COLOR]

---

### Post by efflandt on 2013-04-21
Also having trouble with Steam sounds like a video issue. What video card/chip do you have and video drivers (default, or type and version)? What trouble are you having launching minecraft?

The typical way to launch minecraft (which you can put in a script) is to cd to the directory containing minecraft.jar "launcher" that you downloaded (not the one in ~/.minecraft/bin/ and not a pre-release or test minecraft.jar) is:
```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```(or you can use G to specify GB instead of MB).

---

### Post by Horbo on 2013-04-22
> **soloman469 said:**
> Now i've had enough trouble with TF2. Now i'm having trouble trying to edit the permissions to even LAUNCH Minecraft. Somebody please help this is really starting to tick me off...

[COLOR=#000000]My computer specs:[/COLOR]
[COLOR=#000000]-Ubuntu 12.04 (precise)[/COLOR]
[COLOR=#000000]-Intel(R) Pentium(R) D CPU 3.40GHz[/COLOR]
[COLOR=#000000]-Frequency:3389.176 MHz[/COLOR]
[COLOR=#000000]-L2 Cache:2048 KB[/COLOR]
[COLOR=#000000]-Memory Total:3000 MiB

I got this computer for free from a place called Free Geek if that helps.[/COLOR]

You need to describe exactly what is happening.  Anyone reading this at the moment can only try to guess at what sort of problem you're seeing.

It certainly doesn't sound like anything related to your system specs, either...

---

### Post by soloman469 on 2013-04-22
Omg it worked!!!!!! Thx a lot!

---

