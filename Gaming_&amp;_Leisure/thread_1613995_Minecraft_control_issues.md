---
title: "Minecraft control issues"
date: 2010-11-05
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2010-11-05
Hello !

Today I've bought Minecraft in hopes of playing it.
The game executes fine in Java 6 Runtime and the world loads.
I can control my character via mice (look around, mine), but the keyboard doesn't respond at all (except Alt+F4 which closes the game), I cannot walk, cannot open the inventory cannot play.


```
maximb@MaximB-HQ:~/Games$ java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
Username is 'MaximB'
28
Setting user: MaximB, -4215292293656596749
Loading: net.java.games.input.LinuxEnvironmentPlugin
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

Player is null
Player is null
Player is now null
Loading texture http://www.minecraft.net/skin/MaximB.png
Player count: 1
AL lib: ALc.c:1352: exit(): closing 1 Device
AL lib: ALc.c:1329: alcCloseDevice(): destroying 1 Context
AL lib: alSource.c:2361: alcDestroyContext(): deleting 32 Source(s)
AL lib: alBuffer.c:1081: exit(): deleting 1 Buffer(s)

```

Please help me solve this issue.

---

### Post by MaximB on 2010-11-05
I've made some progress but the keyboard still won't work.
I've run this command to get rid of the permission problems :

```
sudo chmod go=u /dev/input/event*
```

And according to this thread : [http://www.minecraftforum.net/viewtopic.php?f=17&t=18453](http://www.minecraftforum.net/viewtopic.php?f=17&t=18453) the user says : "Problem solved. The culprit was iBus. Quitting it did the trick." but I have none of those processes or files/devices at /dev/input/ or anywhere else.

I hear if you run the game as super user, it works - but that's not a good solution.

---

### Post by UncoElite on 2010-11-05
I've just tried the fix in that thread you linked too and I've tried as root and still no keyboard input

---

### Post by UncoElite on 2010-11-05
I've got it to work. Seems to be an issue with ibus controlling the keyboard.

After fixing the permissions issue I went to System > Adminstration > Language Support
At the bottom of the window change Keyboard Input Method to NONE. Close then logout and back in.
Keyboard worked for me then in Minecraft

---

### Post by MaximB on 2010-11-05
> **UncoElite said:**
> I've just tried the fix in that thread you linked too and I've tried as root and still no keyboard input

Running the game with 'sudo' actually fixes this issue for me, but that's just a temporary solution.

---

### Post by JamesNeko on 2010-12-30
Yeah, it's ibus, which sucks because I actually use it sometimes.

It's hardly elegant, but I've found a `killall ibus-daemon` before playing Minecraft will work - probably have to log in again to get it back, oh well.

I do find it a little annoying that Minecraft grabs *all* keyboard input, even WM keys like Alt-tab or Super-tab (unless Esc is pressed, it seems). Most games seem to get by fine without grabbing *everything*.

---

### Post by donkyhotay on 2010-12-30
write a script that kills ibus, launches minecraft and then restarts it again when the program closes.

---

### Post by tekkamanendless on 2011-06-13
I too use ibus regularly; however, I found that this little gem does the trick:
```
sudo -u doug Minecraft/minecraft
```

Essentially, run Minecraft with sudo *as yourself*.

Of course, "doug" is my linux username and "Minecraft/minecraft" is the path to my Minecraft launch script.

Doing this apprently gets around the problem because a "different" user is now running the application, whereas my "normal" user is the one with the troublesome ibus configuration.

---

### Post by poszest16 on 2012-04-07
Heres the one true fix for the iBus and Minecraft conflict. READY.

\\:D/

Your lwjgl/Lightweight Java Game Libary is outdated (for linux at least). Apparently the developers of LWJGL have already fixed the iBus conflict with an updated library but apparently since not so many people use iBus (ie. I use it for Japanese input) Mojang has neglected to update the library that is shipped with minecraft.

You can update the libraries manually by downloading them from [http://lwjgl.org](http://lwjgl.org) (Be sure to download the binary package). As of writing this reply the latest version is [2.8.3]("http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download") which worked for me on Minecraft 1.1 and 1.2.

Here are some simple steps:
1. Download & Open
2. extract the files "jar/lwjgl.jar, jar/lwjgl_util.jar and jar/jinput.jar" to "~/.minecraft/bin" (Backups Recommended)
3. extract the files "native/linux/*" to "~/.minecraft/bin/natives" (Backups Recommended)

Interesting fix. Before I had this iBus issue, I also was getting a nasty sticky key issue but this update also fixed that. Typical, it started with Atmosphir and now Minecraft, not taking care of their loyal Linux users. Atmosphir was built with Linux users in mine and now they no longer even offer a linux build. Soooo annoying. ](*,)

---

### Post by pualpu on 2012-04-11
> **poszest16 said:**
> Heres the one true fix for the iBus and Minecraft conflict. READY.

\\:D/

Your lwjgl/Lightweight Java Game Libary is outdated (for linux at least). Apparently the developers of LWJGL have already fixed the iBus conflict with an updated library but apparently since not so many people use iBus (ie. I use it for Japanese input) Mojang has neglected to update the library that is shipped with minecraft.

You can update the libraries manually by downloading them from [http://lwjgl.org](http://lwjgl.org) (Be sure to download the binary package). As of writing this reply the latest version is [2.8.3]("http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/lwjgl-2.8.3.zip/download") which worked for me on Minecraft 1.1 and 1.2.

Here are some simple steps:
1. Download & Open
2. extract the files "jar/lwjgl.jar, jar/lwjgl_util.jar and jar/jinput.jar" to "~/.minecraft/bin" (Backups Recommended)
3. extract the files "native/linux/*" to "~/.minecraft/bin/natives" (Backups Recommended)

Interesting fix. Before I had this iBus issue, I also was getting a nasty sticky key issue but this update also fixed that. Typical, it started with Atmosphir and now Minecraft, not taking care of their loyal Linux users. Atmosphir was built with Linux users in mine and now they no longer even offer a linux build. Soooo annoying. ](*,)

brilliant ,it works:lolflag:

---

