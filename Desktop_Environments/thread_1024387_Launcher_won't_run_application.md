---
title: "Launcher won't run application"
date: 2008-12-29
forum: Desktop Environments
---

### Post by Thoht on 2008-12-29
Hi!

I searched Google for various terms related to this but couldn't find anything specifically about this.

I downloaded the Cave Story (Doukutsu Monogatari) Linux port found [here](http://www.cavestory.org/downloads_1.php). It's really neat, but I'm not quite sure I grasped what to do with it since it's not a package. I put it in my home directory, and double clicking the "doukutsu" file will run the program.

Now that makes it a bit messy since I can't launch it by GNOME Do, being a OS X user Quicksilver is the way to go for me.

1) Is it possible to make this a package, so that it will be put in /usr/bin and hence be listed by GNOME Do?

Being a bit on the unexperienced side of all that, I figured I'd just create a launcher for now and put in the panel. However, clicking on that launcher only results in a small black window appearing and then disappearing again in 1-2 seconds.

2) How can I make a launcher for that file?

Thank you in advance!

/T

---

### Post by LightningEagle on 2009-12-08
I know this thread is pretty old, but right now I'm experiencing the exact same problem as stated above. Can't get a launcher for Cave Story working. Same black window opening for a few sec and then closing.

I hope that a reply might come around this time to save my day since I haven't been able to find anything else than this post describing the problem and nothing at all solving it.

anyone... ?

I'm running Ubuntu 9.10 32bit on an AMD Athlon 64 3700+, 3GB ram, Gforce 8600 GTS graphics card if that helps in anyway. 
The cave story linux version was downloaded from this website:
[http://www.miraigamer.net/cavestory/downloads_1.php](http://www.miraigamer.net/cavestory/downloads_1.php)

The game works when launched directly but with a launcher it is messed up.

help... ?

---

### Post by Marson on 2009-12-09
i'm having this problem too... any solution?

---

### Post by gadolinio on 2009-12-09
YAY!!! GOT IT! Read this thread, downloaded the program, tried a bit... and found A way, at least...
I copied all the files in my user folder (this can be somewhat messy, but it's the only solution i've found):
Config.dat,  data(folder),  doc(folder),  DoConfig.exe,  doukutsu,  doukutsu.bin,  libSDL-1.2.so.0

With those files copied in the user folder, create a launcher like this:
Type:
application in terminal

Name:
whichever you want

Command:
sh ./doukutsu
(note the space between "sh" and "./doukutsu")

Comment: anything, even blank.

Single clicking that launcher starts the application. Hope this solves your problem...

---

