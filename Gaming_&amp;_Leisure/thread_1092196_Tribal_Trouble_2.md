---
title: "Tribal Trouble 2"
date: 2009-03-10
forum: Gaming &amp; Leisure
---

### Post by aarceng on 2009-03-10
I want to try the web game Tribal Trouble 2. ([http://tribaltrouble2.com/main.html](http://tribaltrouble2.com/main.html)).

When I go to the site i get a message 

[INDENT]You need to install the Java plugin

To install the Java plugin required to play the game, please click on the yellow bar that has appeared at the top of your browser window:

If you do not see the bar, the plugin is available at the Java website
[/INDENT]

I don't see any yellow bar and as far as I can tell I have Java installed.
What do I do now?  :confused:

---

### Post by FrozenFox on 2009-03-10
The yellow bar it speaks of is for Windows users only; firefox brings open a little yellow bar asking you if you want to install a given component needed. I imagine Ubuntu would change firefox to do something similar themselves eventually. Until then, the same thing can be done in a different, pretty simple way.

I suspect you don't have all of the necessary packages installed, particularly the **plugin** package.

sun-java6-jre sun-java6-plugin sun-java6-fonts

Install those in Synaptic package manager. Or open a terminal and

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

That'll do the same thing.

After it's done, wait a few seconds, close firefox if it's open, re-open it, try again.

Note: I think you need the universe, multiverse, whatnot repositories / download sources enabled or it will nag about some of the above not being available. I believe you can do that pretty easily in synaptic options/preferences/settings. I'd tell you how to do this outright, but I haven't used ubuntu in some time, and it's not too hard to find in google or just by looking around yourself. Also, I get the impression that site needs flash installed too, but I'm not sure. Get flash and the flash plugin packages installed if so. They might be available in the ubuntu-restricted-extras package, I don't remember for sure. Anyway, be sure to post back if that is true or you have further problems :).

---

### Post by aarceng on 2009-03-10
Progress! I can now log in and it appears to load but then ends with a message box saying 

[INDENT]Launching game...
HTTP Status 500 - [/INDENT]

This appears to be a server problem. This has happened on attempts several hours apart. Any suggestions?

---

### Post by yther on 2009-03-10
I just tried that game as a "visiting chieftain" (so I did not log in), and it appeared to work just fine.  I got prompted twice by Java about running the applets, the game downloaded (took about 2 minutes), then it went full-screen.  Graphics worked, there was music, I could click on the little guys and make them run around... then I quit.

I'm on 64-bit Kubuntu 8.10, with Firefox 3.0.6, NoScript extension (I had to approve the site temporarily), AdBlock Plus, Flash 10.0 r22 (32-bit).  Java package is sun-java6-bin, version 6-10-0ubuntu2.

500 seems to indicate an internal error... maybe their server is too busy.  In that case, random people might get that error.

---

