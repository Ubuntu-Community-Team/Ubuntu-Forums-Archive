---
title: "Runescape/browser game problems?"
date: 2010-02-08
forum: Gaming &amp; Leisure
---

### Post by pinnacle2009 on 2010-02-08
I have been trying to play Runescape. On my netbook (Windows 7), it runs fine. When I try on my desktop (Ubuntu), problems arise.

Lag is horrible and I get disconnected randomly.

Runescape is a Java game. I am not sure how to fix the problem other than just suck it up and play on my netbook. lol

Any help here?

---

### Post by ajgreeny on 2010-02-08
Which version of java are you running?  You may have the open source, which is perhaps not as good as sun-java.

---

### Post by pinnacle2009 on 2010-02-08
I believe it may be the opensource.

How do I get Sun Java on Ubuntu?

---

### Post by pinnacle2009 on 2010-02-08
Hmmmm, how does OpenSolaris do with java based applications and games?

At this point, I am only using my desktop for little games like this. I may give that OS a try. Desktop is just turning into a project-learning station! :popcorn:

---

### Post by Hwæt on 2010-02-09
I wrote a PM to a friend about this a while back with pretty detailed instructions for how to get it running correctly on Karmic.

Here is my "howto":

> 
Alright, getting RuneScape to work decently is a bit tricky, and getting HD to work requires a decent graphics card. If you can run RuneScape HD in Windows, then your graphics card is probably capable of running it in Ubuntu.

Applications -> Ubuntu Software Center

Click on it, and search for "OpenJDK"

After that, click on the "OpenJDK Java 6 Runtime" and hit the install button. Now, go back and click on the "IcedTea Java Plugin" and hit the install button.

After that is done, the bare bones of what you need to run RuneScape should be installed. However, to get it working properly, you need to disable Ubuntu's compositing Window Manager, Compiz.

System -> Preferences -> Appearance

Click on the visual effects tab, and check "none". Then, close the window.

However, that is not all. If you have a graphics card made by a certain manufacturer (Nvidia, ATi), then you need to download the proper drivers for 3D acceleration.

System -> Administration -> Hardware Drivers

If anything pops up, try to get the recommended driver and install it by enabling it. If nothing pops up, then you're good to go.

Note: a reboot is required after installing new drivers.


Now, you're set to run RuneScape.

Go to RuneScape's website, navigate to the game, and accept the Java Applet.

Everything should work now, and you may notice the occasional crash. There are no workarounds available for these at the moment, but I've found that cutting off RuneScape's sound makes the game a bit more stable.

Cheers!


---

### Post by NekoMaster on 2010-02-09
> **Hwæt said:**
> I wrote a PM to a friend about this a while back with pretty detailed instructions for how to get it running correctly on Karmic.

Here is my "howto":

Hey man, thanks! Just something else to play now, was getting bored of play openTTD

---

