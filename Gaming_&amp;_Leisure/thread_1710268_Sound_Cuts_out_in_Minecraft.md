---
title: "Sound Cuts out in Minecraft"
date: 2011-03-19
forum: Gaming &amp; Leisure
---

### Post by Joseph Schwenker on 2011-03-19
In Minecraft multiplayer, I have been having an issue with the sound cutting out after a period of time. I have not yet seen this in singleplayer. Here's the output:

```
java -Xmx1024M -Xms1024M -jar minecraft.jar 

(<unknown>:6778): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-cA9Lhcae30,guid=78602da05e2606e9280a82cd000000d1 failed: Failed to connect to socket /tmp/dbus-cA9Lhcae30: Connection refused.
28
Setting user: ZombieRamen, 3504847628368975376
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

143 recipes
Stopping!

SoundSystem shutting down...
AL lib: alBuffer.c:1081: exit(): deleting 3 Buffer(s)
    Author: Paul Lamb, www.paulscode.com

joseph@joseph:~/Downloads$ java -Xmx1024M -Xms1024M -jar minecraft.jar 

(<unknown>:7228): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-cA9Lhcae30,guid=78602da05e2606e9280a82cd000000d1 failed: Failed to connect to socket /tmp/dbus-cA9Lhcae30: Connection refused.
28
Setting user: ZombieRamen, -5317663326725129912
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

143 recipes
java.net.SocketException: Connection reset
	at java.net.SocketInputStream.read(SocketInputStream.java:185)
	at java.net.SocketInputStream.read(SocketInputStream.java:199)
	at java.io.FilterInputStream.read(FilterInputStream.java:83)
	at hz.b(SourceFile:113)
	at lt.c(SourceFile:155)
	at lt.c(SourceFile:9)
	at sj.run(SourceFile:62)
stopStopping!

SoundSystem shutting down...
```

Any ideas?

---

### Post by Joseph Schwenker on 2011-03-20
bump

---

### Post by ubudog on 2011-03-22
Yep, this happens to me too...

---

### Post by abexy on 2011-03-22
I am having the same issue. After about 30 seconds in multiplayers the sound cuts out. I also noticed the CPU usage for Java jumps to over 100% (it said 114 for me last time) and pulseaudio was at -11%. This has happened to me before in singleplayer, but after a much longer period of time and only a few times.

---

### Post by abexy on 2011-03-22
I found a solution in this thread which seems to be working:

[http://ubuntuforums.org/showthread.php?t=1613942](http://ubuntuforums.org/showthread.php?t=1613942)

---

### Post by ubudog on 2011-03-22
> **abexy said:**
> I found a solution in this thread which seems to be working:

[http://ubuntuforums.org/showthread.php?t=1613942](http://ubuntuforums.org/showthread.php?t=1613942)

Cool, thanks.  I'll try that.  Hope it works!

---

### Post by Joseph Schwenker on 2011-03-22
Thanks for the suggestion. I'll try it soon.

---

### Post by Joseph Schwenker on 2011-03-23
I tried both of those in multiplayer, but I"m still having my sound cut out. It's weird, because I have no problems in single player, even when using Skype. In multiplayer, however, if I use Skype, the sound cuts out, even with those solutions.

---

### Post by Joseph Schwenker on 2011-03-28
bump

This issue still occurs.

---

### Post by Joseph Schwenker on 2011-03-30
I'm experiencing this issue even when Skype is not running. Padsp does nothing. pasuspender java -jar minecraft.jar returns some error about "-j" not being valid.
I also tried padsp java -Xms1024M -Xmx1024M -Djava.net.preferIPv4Stack=true -jar minecraft.jar
but still lost sound.

I also found that when the sound cuts out, the graph (it comes up when you press F3) makes a humongous short spike.

---

### Post by Joseph Schwenker on 2011-04-03
This issue continues to occur no matter what command I use. If I run it from the terminal and the sound cuts out, upon trying to exit Minecraft, Minecraft will take longer than usual, and the terminal will be stuck on "Stopping Sound System" until Minecraft finally exits.

---

### Post by Joseph Schwenker on 2011-04-19
Problem still persists in SMP in 1.5 Beta.

---

### Post by Joseph Schwenker on 2011-04-21
bump
I've tried padsp; nothing works.

---

### Post by jynyl on 2011-05-16
Ditto: same problem here; sound randomly cuts out in Minecraft.

Running Kubuntu 11.04 with sun-java6.

---

### Post by Joseph Schwenker on 2011-05-16
The problem *might* related to running a a Minecraft Beta listen server.

---

### Post by jynyl on 2011-05-19
So, what is a "Minecraft listen server"?

Do you have to actually start this, or does it run automatically?

I'm running Minecraft in single user mode, without any server (that I know of).

---

### Post by Joseph Schwenker on 2011-05-19
> **jynyl said:**
> So, what is a "Minecraft listen server"?

Do you have to actually start this, or does it run automatically?

I'm running Minecraft in single user mode, without any server (that I know of).

A Minecraft listen server is just a regular Minecraft server run from the same computer that the operator plays on. The sound cuts out more often when I'm running and playing on a Minecraft server on the same computer than if I play on someone else's server, or even on single player.
Nonetheless, I've still had sound crashes in single player, multiplayer, and multiplayer with a server running on the same computer.

---

### Post by Joseph Schwenker on 2011-07-06
I've found a [fix]("http://www.minecraftforum.net/topic/134703-linux-stuck-keys-solution/") that *might* fix the problem.

From my understanding, this fix just replaces Minecraft's dependencies with newer ones. Though this fix is intended to stop keys from getting "stuck" in Minecraft, it might also fix audio problems, since an audio library is part of the package.

---

### Post by Kodeine on 2011-07-10
I was also getting this. It didn't really happen too often for me but hopefully it won't happen at all now thanks!

---

### Post by Joseph Schwenker on 2011-07-10
After applying the fix and <s>testing</s> playing Minecraft for several days, I can confirm that this fix fixes pretty much every problem I've had with Minecraft on Linux, including sound and the stuck keys glitch. I highly recommend that you apply this fix. One word of warning, though: you will have to delete your ~/.minecraft directory and apply this fix again whenever Minecraft updates, otherwise Minecraft won't be able to open correctly. **Be sure to back up your screenshots and saves subdirectories before deletion!**

---

