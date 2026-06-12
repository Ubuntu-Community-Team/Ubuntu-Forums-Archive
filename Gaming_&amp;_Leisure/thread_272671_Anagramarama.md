---
title: "Anagramarama"
date: 2006-10-06
forum: Gaming &amp; Leisure
---

### Post by tulsh on 2006-10-06
This game worked just fine and after I rebooted my computer it will not work anymore.  It trys to start and then goes away.  I went to add/remove in applications and did an uninstall and then reinstalled it.  No good, still doesn't work.

---

### Post by Perfect Storm on 2006-10-07
Try start it through the terminal. What does it say?

---

### Post by tulsh on 2006-10-10
At the cost of really sounding dumb, how do you do that?  I don't know what to put into the command line to start an application.
Thanks for your help.

---

### Post by Perfect Storm on 2006-10-10
Well the first option would be just writting the name of the game in the terminal (with lower letters).

---

### Post by MrBlond83 on 2006-10-10
Open the terminal window and try just typing the game's name. or do anag and then press tab :)

---

### Post by tulsh on 2006-10-10
cool it started with just the complete name in the terminal!
Thanks

---

### Post by tulsh on 2006-10-10
The program flashes up on the screen and then diappears and this comes up. "Unable to open audio" is the message that I get when I try to run it in the terminal.

---

### Post by tulsh on 2006-10-10
Do you have an suggestions about what to do when the program begins to come on the screen and then goes away?  When I started it in the terminal, it says "unable to open audio".  I am trying to fix this for my invalid neighbor.
Thanks

---

### Post by Neobuntu on 2007-09-19
I'm having the same problem. I tried different sound server settings but is still says Alsa problems. This after setting to alsa.

What's the deal with sound in ubuntu anyway?

---

### Post by cogadh on 2007-09-19
Wow, could you have found an older thread to resurrect?

What do you mean by "the deal with sound in ubuntu"? With the exception of the annoyance of sound volume turned all the way down by default, it works perfectly (at least on my system).

EDIT - I just installed Anagramarama and sound works fine. What SDL libraries do you have installed?

---

### Post by Neobuntu on 2007-09-22
Hey.

LOL, I'm not saying sound is bad. I just have a few glitches.

Anangramrama (kids love it) will not run; due to it's stated sound issue.

I'm confused about which sound setting to use. Sometimes one app works one way and another, set differently.

So, I was wondering about the general health on sound; with OSS and Ubuntu.

Right now (For example), sound on TORCS works but Kopete sounds do not.

---

### Post by cogadh on 2007-09-23
I think your confusion may have to do with the fact that Ubuntu uses ALSA by default, not OSS. OSS has been pretty much abandoned as a Linux standard and ALSA has become its replacement (as of the 2.6 kernel series, ALSA is the default sound system in Linux). 

However, some applications do still require OSS to work (Kopete maybe?). That can sometimes be worked around by using the ALSA OSS wrapper to run an application (you can get it from the Ubuntu repositories, just search for "aoss" in Synaptic).

Anagramarama does not require OSS to run, and as long as you have the correct SDL libraries installed, it *should* work.

---

### Post by R33D3M33R on 2009-03-18
I have two questions:

How to select the language/dictionary?
Is there any better English dictionary available? The current one has tons of weird words in it.

Thanks!

---

