---
title: "New Strategic RPG Dungeon Crawler for Linux/Ubuntu - free for beta test download"
date: 2014-11-02
forum: Gaming &amp; Leisure
---

### Post by kraset on 2014-11-02
Hello Ubuntu Users!
(EDIT: OOPS sorry, I posted in the wrong forum, thanks for move!)

I am soon going to release a game that I hope work well on Linux, and I start to reach out the the Ubunty community becuase it's very big, and maybe someone here would care to run just a little test of it.
Yesterday, I tried to install Xubunty myself on Virtual box with the goal to verify the game myself on Linux, but failed due to some cryptic message.
So I gave up and now, I'm sending a link to you guys, of my fully implemented soon-to-be-released version of my game, "Lord of th Dark Castle".
The game runs in Java, and has been verified to work great on Mac and PC with various screen resolutions.

This game is called "Lord of the Dark Castle" - **a casual turn-based retro style roguelike dungeon crawler with elements of strategy**. 
The game can be found here:
**[EDIT: the current version freezes on Ubuntu because of a crash in Java Sound vs Pulse Audio. Same code works fine on PC and Mac, btw...]**
You can read about the game here, but don't bother installing yet until there is a solution on the Sound Issue!
**[http://lordofthedarkcastle.freeforums.org/game-download-link-latest-t4.html](http://lordofthedarkcastle.freeforums.org/game-download-link-latest-t4.html)**

I've written the game myself (about 6 full man months development time) and I've spent about $3000 on licensed art work so far. So I hope to sell the game for a couple of bucks at GameFly, GoG and Steam. Also, if you know any more good forums to sell games for Linux, I'd be happy to know about it.

For now, the game is completely free to download during this last Beta-test stage. I'm waiting for a last delivery of some improved graphics, so I will be adding that and some sound effects as the last iteration.
Feel free to register at my game forum linked above to give some feedback. Registration is just optional and you can download the game without registering.

Best Regards
/Christian Andersson, Craze Creative Studios

---

### Post by bapoumba on 2014-11-02
*Thread moved to **Gaming & Leisure**.*

---

### Post by pqwoerituytrueiwoq on 2014-11-02
if your issue was 
something something permissions something executable something
you need to chmod +x the jar file
.zip does not preserve permissions like .bz2. and .gz

---

### Post by kraset on 2014-11-02
No, regarding my problems with Virtual Box it was:
VT-x is not available.  (or something like that)
... then I did some workaround suggested here (because I did not want to go in and change in my BIOS just because running Virtual Box)
[https://forums.virtualbox.org/viewtopic.php?f=6&t=58820](https://forums.virtualbox.org/viewtopic.php?f=6&t=58820)
"VBoxManage modifyvm <vmname> --longmode off"
... and then I ended up in Kernel Panic.
... and then I tried a couple of other things, and then I gave up.
No big deal.

---

### Post by pqwoerituytrueiwoq on 2014-11-02
i can confirm it does fire up, though my xfce4-panel is above the game
[[IMG]http://www.zimagez.com/miniature/screenshot-11022014-021211pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-11022014-021211pm.php")
maybe it is running maximized in borderless mode and not fullscreen

BTW VT-X is a option you need to enable in your bios to boot a 64bit OS in virtualbox, some intel CPUs don't support this feature (cause they wanted you to buy the higher end chip to get it)
i have found 32bit to be unstable with my laptop in virtualbox (CPU does not support VT-X)

---

### Post by kraset on 2014-11-02
Thank you for very much for testing!

To achieve full screen, I am using Java:
  setExtendedState(JFrame.MAXIMIZED_BOTH);
  setUndecorated(true);
and it works well on PC. But on Mac, the Menu Bar is shown on top. Seems to be similar here...

There is one strategy I haven't tried. Someone adviced that it might work on Mac as well. Using the GraphicsDevice, as suggested here.
[http://stackoverflow.com/questions/11570356/jframe-in-full-screen-java](http://stackoverflow.com/questions/11570356/jframe-in-full-screen-java)

But it felt kind of low-level-API-like to do that. Since the "high-level" API works on PC, I settled with that. Of course, now... I may have to reconsider...  It does look kind of ugly, doesn't it?

Best Regards
/Christian

---

### Post by kraset on 2014-11-02
... actually, I'm reading again on the topic right now. What I felt was kind of low-level-API seems to be the right thing to do if Full-screen-exclusive mode is supported by the system. It may even increase performance.
[http://docs.oracle.com/javase/tutorial/extra/fullscreen/exclusivemode.html](http://docs.oracle.com/javase/tutorial/extra/fullscreen/exclusivemode.html)

... so I think I'll give it a go, and maybe that solves the thing on Mac too.

---

### Post by kraset on 2014-11-06
I managed to get Virtual Box up'n'running on a laptop and noticed the following:
- The current version freezes on Ubuntu because of a crash in  Java Sound vs Pulse Audio. Same code works fine on PC and Mac, btw...
I updated with a no-sound version for Linux users **(not an official release though... it's only possible to run the game in test/debug-mode in this version).**
[http://craze.se/lotdc/NoSound.zip](http://craze.se/lotdc/NoSound.zip)
- It's a good idea to create a launch script, some .sh file to do the same that's done in the StartGame.bat file.
- It's a good idea to toggle the +x flag on the main .jar file
(So I will prepare that for future Linux distributions)

Now... I have to try to get the sound working for Java on Linux. I googled this Pulse Audio crash and tried a couple of workarounds... an yeah...getting rid of the crash was not a problem. But the game still hangs when the music starts playing, without any error message whatsoever.  I will post a separate thread on this. Note that I am using Java Swing and not Java FX. So I cannot use the latest Media components from Java FX.

The real FullScreen mode is now used. The message when I start up the game says: Full Screen supported, enabled. It speeded up the game considerably. Still the top Ubuntu menu is visible on Linux, so it seams that Java FullScreen mode does not work 100%, at least not on my 14.04 Xubuntu.

Best/C

---

