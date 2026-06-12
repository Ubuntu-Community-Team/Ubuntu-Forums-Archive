---
title: "Minecraft.jar problems"
date: 2012-10-09
forum: Gaming &amp; Leisure
---

### Post by Treyonator56 on 2012-10-09
I downloaded the full version of Minecraft today, and it seems to be really fun. The only problem I have, is that the mouse doesn't seem to stay focused in the Minecraft window. Usually, you would have to hit Esc to pause the game, and go to a different window. On my computer, I move my mouse around, and it doesn't stay with the crosshairs in the middle of the screen. I'm not really sure what happens, but my guess is that it thinks I clicked outside of the window, so I lose control of the mouse. I can still use the keyboard, just no mouse. To fix it temporarily, I have to hit the "e" key for inventory, and hit it again. Then I have control over my mouse until it happens again. Can anyone help me with this, and sorry if this is unclear. I've tried my best to explain it, but I really don't know whats going on.

Note: I played the exact same version on Windows, and it ran fine. No mouse/window problems at all. Oh, and my OS is Lubuntu.

---

### Post by IWantFroyo on 2012-10-09
This might be an issue with your jre.

Try installing the openjdk-7-jre package, and removing openjdk-6-jre. It might work better.

---

### Post by Treyonator56 on 2012-10-09
The only reason why I have OpenJDK6 installed, is because of Netbeans. Can I make NetBeans use OpenJDK7 instead? I remember installing NetBeans and it came with OpenJDK6.

Edit: I ran Minecraft with OpenJDK7, and the same thing still happened. Surely that can't be the problem. :(

---

### Post by IWantFroyo on 2012-10-09
Hmm...

The only time I've ever had this issue is when using a touchpad. I was accidentally clicking when moving my finger around.

I fixed it by going to the Mouse settings, going to the Touchpad tab, and unchecking the "Click with touchpad" setting.

---

### Post by Treyonator56 on 2012-10-09
These are the only input settings i have. 

[IMG]http://i45.tinypic.com/2r77gnm.png[/IMG] 

And here are the only mouse settings i have. 

[IMG]http://i50.tinypic.com/15mjkfk.png[/IMG]

Doesn't look like there is anything about that in there. 

I'm going to try running it in OpenJDK6. I'll see if that helps some how.

Edit: When I play the game, I don't use the touchpad at all either. I use a USB mouse instead.

Playing it on JDK6 doesn't help at all, actually, I think its worse.

---

### Post by IWantFroyo on 2012-10-10
Then you shouldn't have issues with the mouse.

It must be with window focus. Maybe the system thinks the mouse is going over other windows?

There should be a way to adjust window focus settings in Ubuntu. I just can't remember it at the moment, and I'm using Fedora. :(

---

### Post by Treyonator56 on 2012-10-10
This is really strange. I even went to full screen view, and it still didn't work right. Guess I'll have to find an alternative to Minecraft for Linux.

---

### Post by efflandt on 2012-10-13
I have been running minecraft since its 1.8 beta (before 1.0 release) in 64-bit Ubuntu w/openjdk-6 and never had the problem you describe in regular minecraft. I have also run it on both 64-bit Ubuntu and Lubuntu that share a common /home partition, but not that frequently because it is a 1 GHz 2 core tablet PC w/10.1" 1280x800 screen.  On that or desktop on 32" 1080p HDTV I typically run full screen, not in a window. 

The only thing I can think of is that classic X from years ago would typically only focus on the window the mouse cursor was actually on at the time, instead of the last window clicked.  So under Openbox Configuration Manager > Mouse > Focusing Windows, make sure that "Focus windows when the mouse pointer moves over them" is NOT checked.  Although, if that was checked it would also tend to move keyboard focus.  So if it is a laptop, maybe it has something to do with dragging a thumb on the mousepad.

I usually go to less than full screen when switching to a different workspace to check the minecraft wiki in a web browser, because sometimes when I do that full screen, the keyboard does not respond when I go back.  But if I just pick up something out of my inventory with the mouse and put it back in, the keyboard works.

The only time I have had the in game mouse cursor freeze is with tekkit (which is a separate minecraft with a bunch of mods added) and not even sure when that happens, possibly when closing the gui for one of the mod tools.  But if that happens, I just hit "E" twice (to go into inventory and back to game) and it clears up.

You may want to upgrade lwjgl.  v2.4.2 distributed with minecraft occasionally results in stuck movement keys (press key in same direction you are moving to release a stuck key).  So I have been using lwjgl 2.6 (most recent is 2.8.4).  It is a zip file that involves replacing files in ~/.minecraft/bin and natives subdirectory under that.

---

### Post by BlueBinary on 2012-10-13
Have you tried the in-browser version? I had this problem awhile ago, but the browser version worked fine for me.

---

### Post by Treyonator56 on 2012-10-13
@effladft thanks for all that information. I'll try some of it and tell you how it turns out.           

@blue, I've tried that in chromium and the iced tea plugin always crashes.

---

### Post by Kubko on 2012-10-13
its caused by minecraft using old lwjgl version, just get download the newest version from 
[https://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.4/](https://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.4/)

and unzip and replace(minecraft stores lwjgl files in ~/.minecraft/bin

---

### Post by Treyonator56 on 2012-10-16
I found the lwjgl that I needed, but the Minecraft archives didn't have a bin folder. So, I just put the files in with everything else. I'm not sure if it will work though. :s

Edit: Nope, it didn't work. I checked, and the Minecraft files were last edited in 2010. Does that mean its not compatible with the lwjgl?

---

### Post by efflandt on 2012-10-18
When you mention that you do not find a bin in the Minecraft archives, I see at least one thing wrong.

The **minecraft.jar that you download** from [www.minecraft.net]("http://www.minecraft.net") **is just a launcher** (Internet Explorer may incorrectly save it as minecraft.zip).  Once you cd to the directory with that minecraft.jar launcher and run it with:

```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

```it creates a hidden .minecraft directory in your personal home dir (ie, ~/.minecraft) where it keeps all the working files for the game including a different ~/.minecraft/bin/minecraft.jar that is the actual current version of the game.  Alway use the minecraft.jar launcher to start the game, NOT ~/.minecraft/bin/minecraft.jar.

To see hidden folders that begin with a dot, either hit Ctrl+H in the file viewer, or include -a in ls options (like: ls -al).

That is where you find the files that match names in a newer lwjgl.zip in .minecraft/bin/ and .minecraft/bin/natives/.  If you want it to use more RAM (preferably 64-bit Linux) you could up the launcher to **-Xmx2G -Xms1G**, etc.

You do not necessarily need Oracle (formerly Sun) Java, it works fine with openjdk-6 or openjdk-7.

Still not sure how your cursor gets outside of the minecraft window and freezes your in game cursor.  The only issue I have had with the original lwjgl 2.4.2 is occasional stuck movement keys.(W, A, S, D).  The only way I can move the cursor outside of the minecraft window is if is if I am looking at my inventory (E), the gui of a device (chest, furnace, etc.), or Esc.

---

### Post by DarkAmbient on 2012-10-21
First thing that came to mind was what other before me mentioned, "outdated" lwjgl-files. Feel free to try "Minecraftinstaller" linked in my sig., it can do that among else. :)

ps. Once downloaded, you need to make it executable to be able to run it as an app/program.

---

### Post by holastickboy on 2012-10-23
The official website also mentions using oracle java, not the openjdk mentioned previously.check out this link to install oracle java 7 via apt.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

