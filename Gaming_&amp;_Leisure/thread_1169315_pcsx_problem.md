---
title: "pcsx problem"
date: 2009-05-25
forum: Gaming &amp; Leisure
---

### Post by tommah04 on 2009-05-25
the game starts super fast, then just freezes and I have to force quit

could it just be the game, or what?

---

### Post by hikaricore on 2009-05-25
You're going to have to provide a few more details if anyone is going to help you.

What game?
What does pcsx output to the terminal when it locks?
What video hardware/drivers are you using?
Which video plugin are you using and have you tried adjusting the settings?
Etc.

Basically as much info as you can provide the more help you're likely to get in return.
It's not always the care but it helps . :p

---

### Post by tommah04 on 2009-05-25
tom@tom-desktop:~$ pcsx
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
Loading memory card /home/tom/.pcsx/memcards/card1.mcd
Loading memory card /home/tom/.pcsx/memcards/card2.mcd
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
RGB not found.  Using YUV.
DFInput: starting thread...
DFInput warning: device already initialized.

game is DBZ: Legends, but so far that's the only game I've gotten ANYthing out of

looks like DFInput is the obvious problem, but I'm not really sure what that is, prolly a graphic?

that's everything from starting, loading iso, the start of the game, and freezing

---

### Post by tommah04 on 2009-05-25
just tried Legend of Mana and that freezes after the first couple of opening credits also

---

### Post by sp0tz on 2009-05-25
I couldn't get pcsx running very well either, and tried a good 5 or 6 games. 

Try pSX, maybe? I wrote a guide....
[http://ubuntuforums.org/showthread.php?t=1169703](http://ubuntuforums.org/showthread.php?t=1169703)


Either way, good luck.

---

### Post by BoyOfDestiny on 2009-05-25
> **tommah04 said:**
> just tried Legend of Mana and that freezes after the first couple of opening credits also

Okay, I can tell you that Legend of Mana works just fine in pcsx (I'm even using the internal HLE bios.)

I'm running a version of pcsx-df newer than the one in the Ubuntu repos though.
[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

Below is a picture of my settings, including controller inputs.

If that doesn't do it, I can walk you through compiling pcsx-df or if you are running Ubuntu 9.04 and 32-bit, I can provide a deb for you in that case.

---

### Post by tommah04 on 2009-05-25
ok, so I got all excited cause Legend of Mana randomly started working... made my character and everything.....

but once I get passed the opening scene/song, it freezes again

still getting these errors

RGB not found.  Using YUV.
DFInput error: could not open device /dev/input/js0!
DFInput warning: device already initialized.

btw: thanks for the configs, but that's pretty much what mine are too

---

### Post by BoyOfDestiny on 2009-05-25
Alright, maybe there is an issue with sound, so I posted that config too. However, the dfinput thing is odd, you've configured a controller I'm guessing... Also, if you have a "speed" problem, make sure Auto FPS Limiting is ticked in the pcsx Video driver config

So, if you do have Ubuntu jaunty, 32-bit, I've posted a simple deb to install.
After installing, go to Configuration -> Preferences in pcsx, 
Path to Plugins:
/usr/local/lib/games/psemu

See if that solves it, it may just be a bug with the old version.
[http://rapidshare.com/files/237243129/pcsx-df_1.10-1_i386.deb.html](http://rapidshare.com/files/237243129/pcsx-df_1.10-1_i386.deb.html)
MD5: 4FB4FE960B16012AE3C6C3A201257AC4

---

### Post by tommah04 on 2009-05-25
your sound config was different from mine so I changed it... but it didn't help at all

and I'm using 64 bit jaunty

*edit*
yea I tried getting a controller, but it doesn't work :-\

---

### Post by BoyOfDestiny on 2009-05-25
Well, can't make a 64-bit deb at the moment... 

One other thing, what is your memory card configuration in pcsx? 
Make sure you've formatted both memory cards (virtual of course.) 

Maybe the emulator is crashing when the game is checking those, and finds no space to save.

---

### Post by disturbedite on 2009-05-25
> **sp0tz said:**
> Try pSX, maybe? I wrote a guide....
[http://ubuntuforums.org/showthread.php?t=1169703](http://ubuntuforums.org/showthread.php?t=1169703)

i agree, i recommend pSX unless one prefers to use plugins.

---

### Post by tommah04 on 2009-05-25
yea, I just tried reformatting both memory cards

---

### Post by Greg_savieo on 2009-11-06
I am also having this same issue with Legends of Mana, after OP is freezes. I have all my settings the same as what you've recommended.

I am having some issues installing and compiling the data from the developmental version of Pcsx-df.

I am new to the whole terminal and command prompt. could someone help me out?

---

### Post by RusitoQbano on 2010-07-19
The link doesn't work anymore
 
 
> **BoyOfDestiny said:**
> Alright, maybe there is an issue with sound, so I posted that config too. However, the dfinput thing is odd, you've configured a controller I'm guessing... Also, if you have a "speed" problem, make sure Auto FPS Limiting is ticked in the pcsx Video driver config
 
So, if you do have Ubuntu jaunty, 32-bit, I've posted a simple deb to install.
After installing, go to Configuration -> Preferences in pcsx, 
Path to Plugins:
/usr/local/lib/games/psemu
 
See if that solves it, it may just be a bug with the old version.
[http://rapidshare.com/files/237243129/pcsx-df_1.10-1_i386.deb.html](http://rapidshare.com/files/237243129/pcsx-df_1.10-1_i386.deb.html)
MD5: 4FB4FE960B16012AE3C6C3A201257AC4

---

