---
title: "Word Slinger for Linux?"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by Zipster90 on 2007-11-24
I've recently been considering switching one of my aunts to Linux. She's tired of her computer being messed up by kids, grandkids, and other relatives installing crap on her computer, and I'm tired of going to fix it. All she uses it for is web, e-mail, and a particular game that she is unnaturally addicted to.

Word Slinger.

That's all that's keeping me from asking her to switch. I'm sure if it was any other human being they would be fine with letting go of the game, but this is not just any other human being. She's obsessed with this game. If I even brought up the possibility of taking it away I would fear for my life. 

All of this brings me to my question. Does anyone know of any game compatible with Linux that is similar, or at least as addicting, as Word Slinger? 

Don't ask me what the object of the game is, since I'm always too busy *fixing* her computer to play on it. Thanks in advance.

---

### Post by LinuxGamer on 2007-11-24
Well, from what I can tell, there are several places to play it online, and it is a Flash game, so will run just fine on Ubuntu.  Now, I see there is an offline version, that seems to require installation and running.. Do not know enough about it to suggest if it could be run in Linux somehow.

---

### Post by LinuxGamer on 2007-11-24
After further testing, I downloaded and installed the .exe trial version, and it installed with wine from the 7.10 repositories, and ran perfectly after I installed the gecko engine.(Which it prompted me to do when it tried to run after installation.

So convert away! :)

---

### Post by LinuxGamer on 2007-11-24
The only problem I have encountered, your Aunt would not if she has the full version.  In the trial version, when it shows the time left on your demo, my adblocker seems to block it, and there for I have a blank window popping up.  After I close that though, the game pops up and plays and looks nice. It is kinda addictive. :)

---

### Post by Zipster90 on 2007-11-25
Great! I'll see about doing this, then. Thanks a lot! :guitar:

---

### Post by Zipster90 on 2007-11-25
Okay. I've installed Word Slinger on my laptop to try it out. It installed flawlessly, but whenever I try to run it, nothing happens. It doesn't prompt me to install the gecko engine or anything. Any settings in Wine I need to change?

---

### Post by LinuxGamer on 2007-11-25
My install of wine is default.  I did set the sound and stuff, but that is it.  I installed it on my friends laptop today also, and it worked just fine again.  I just installed wine, ran the config and opened each tab. Hit Ok, and everything worked.  Each of the machines I have installed it on had some basic 3d, but that should not matter, it is a pretty low end game for requirements.
Did you get any windows popping up or anything?  If you open a terminal, and enter :
env WINEPREFIX="/home/yourhomedirname/.wine" wine "C:\Program Files\Word Slinger\WordSlinger.exe"
(make sure to set your directory name where I put yourhomedirname)
What happens?  If you get a blank window popping up, try just closing it and see what happens. That for me launches the game like I said.

---

### Post by Zipster90 on 2007-11-26
I'll just see about reinstalling wine. I've changed a few settings since I first installed it. It would probably do it good to have a nice reinstall.

---

