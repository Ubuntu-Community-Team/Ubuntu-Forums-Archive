---
title: "Minecraft Problem"
date: 2010-10-16
forum: Gaming &amp; Leisure
---

### Post by Luke_Todd on 2010-10-16
I did a quick search and I couldn't find anything similar to this, even tried doing the black screen fix to get it to work, but to no avail.

I'm very, very new to using Linux so sorry if it's something very obvious.

Here's the problem, whenever I run minecraft, no problems, I get to the menu fine and everything, it's just when I choose single player and then click on an "-empty-" world that the game freezes and then a crash report comes up, before any part of the actual map is loaded.

This is the crash report I get:
> --- BEGIN ERROR REPORT a1dce528 --------
Generated 16/10/10 12:05

Minecraft: Minecraft Alpha v1.1.2_01
OS: Linux (amd64) version 2.6.35-22-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.5
OpenGL: ATI Radeon HD 4300/4500 Series version 3.3.10237 Compatibility Profile Context, ATI Technologies Inc.

java.lang.RuntimeException: Failed to check session lock, aborting
    at cn.<init>(SourceFile:168)
    at cn.<init>(SourceFile:144)
    at net.minecraft.client.Minecraft.b(SourceFile:1110)
    at jq.c(SourceFile:68)
    at jq.a(SourceFile:54)
    at bh.a(SourceFile:69)
    at bh.e(SourceFile:115)
    at bh.d(SourceFile:103)
    at net.minecraft.client.Minecraft.i(SourceFile:953)
    at net.minecraft.client.Minecraft.run(SourceFile:589)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT 71f76a8e ----------Thanks for any help!
-Toddy

---

### Post by viralmeme on 2010-10-16
> **Luke_Todd said:**
> whenever I run minecraf.. and then click on an "-empty-" world that the game freezes

[Failed to check session lock, aborting]("http://www.minecraftforum.net/viewtopic.php?f=1013&t=22765")

---

### Post by Luke_Todd on 2010-10-16
Erm, yes.

That didn't seem to help slightly, because I don't even understand that solution, as in that page doesn't seem to clearly say what the solution is, do I need to generate a world separately, or is it something else, if so, how do I do that?

-toddy

---

### Post by viralmeme on 2010-10-16
> **Luke_Todd said:**
> I don't even understand that solution
"[COLOR="Blue"][SIZE="2"]It was just an issue with the world... Generated a new one and now it's working[/SIZE][/COLOR]"

You should also try and post the issue on the [MineCraft]("http://www.minecraftforum.net/") forum, I would imagine they would be more able to provide a solution.

---

### Post by Luke_Todd on 2010-10-16
Okay let me explain a little more in-depth seeing as my first post couldn't have been very clear.

Step-by-Step:

**1.** I press Single Player.
**2.** I press "-empty-.
**3.** The application hangs.
**4.** Crash Report appears.

No **generating** is even happening so how can I possibly **generate** a new one, when I can't even **generate** **one** in the **first place**?

However thank you for your help, I will try the MineCraft one as well!

-toddy

---

### Post by ubun7uxx on 2010-12-29
did you ever fix this?  And where did you post in the minecraft forums? I can't find anything on this specific problem

---

### Post by ksaul on 2011-01-12
I too am having trouble with minecraft / java 3d apts. 
After about 3-5minutes of game play, my computer freezes and then i have to shut it down and restart.. there has got to be a solution?

i think it is Java not minecraft causing the problem

---

### Post by acornty on 2011-01-13
you could always just try running minecraft with regular sun java and not openJDK

---

### Post by ExileAmongYou on 2011-01-13
> **acornty said:**
> you could always just try running minecraft with regular sun java and not openJDK

To do this, open up a terminal and run

```
sudo update-alternatives --config java
```

You should see something that looks like this:

```
 Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

```

Type the number next to the one that says java-6-sun. If that option isn't there, try running

```
sudo apt-get install sun-java6-jre
```

then run through the steps again.

Hope that helps. You'll get the hang of all this stuff sooner than you think.

---

### Post by Squeazer on 2011-01-17
I have this problem too. I launch minecraft (with "java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame") and when i try to generate a new world / enter a server it crashes. Here is the error report: [http://pastebin.com/xJdips41](http://pastebin.com/xJdips41)

Running with sudo does not help, it still crashes. How can we fix this?

P.S. I have an ATI Graphic card (HD 4870)

---

### Post by loafimus on 2011-01-28
go into your minecraft directory/world and chmod o+rw on the session.lock file.

restart the minecraft server and it should work.

---

### Post by checksumfail on 2011-06-23
Sorry to necro but this thread shows up in a google search so I thought I'd add that what loafimus said worked for me but I also had to chmod the 'world' directory too.

---

