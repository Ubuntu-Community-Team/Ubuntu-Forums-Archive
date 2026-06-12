---
title: "I'm having trouble figuring out Joy2Key...."
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by richardwad1 on 2007-06-17
I went through the readme file and that only confused me more. I want to configure joy2key to work with xmame and I can't even figure out how to run joy2key. I've found a fe wpeople talking about it on google, but they were having specific problems with it....not really problems starting it. Any help would be appreciated. I guess you can tell I'm new to linux.

---

### Post by Cappy on 2007-06-17
```
sudo apt-get install joy2key
```

to run it should be
```
joy2key
```

---

### Post by richardwad1 on 2007-06-17
I've already gotten that far, but I don't know what to put after joy2key in the terminal. Just typing that brings up a message that tells me what joy2key is then says "Must specify a target!"

---

### Post by buttons on 2007-06-17
You aren't alone in confusion.  Joy2Key is the most ill-documented piece of software I've come across in years.
```
cat /usr/share/doc/joy2key/examples/joy2keyrc.sample 
```
That's my only advice.  Don't even bother with the man file or you'll do your own head in.

I used this once and managed to get it working with some java NES emulator embedded in a webpage, where I had to run joy2key and then click on the open window, then start the emulator.

You'll want to have at least this much in your ~/.joy2keyrc :
```
COMMON
-X
-dev /dev/input/js0
-thresh -15715 5684 16383 -13709 15046 -10365 11034 -13375

```

Assuming your joystick is /dev/input/js0, and you want this for an X-window based game.  If it's fullscreen or console check the examples file.  The thresh values are in the form low hi low hi, and you can get your own values by running the program by itself, ie:
```
joy2key -dev /dev/input/js0 -terminal
```

Again...this program is really obnoxious.  If you're fed up with it (and I certainly wouldn't blame you if you were) a search in synaptic shows "xjoypad" which seems to do the same thing, but I don't have any experience with it.

Good luck.

---

### Post by richardwad1 on 2007-06-17
Thanks for the help! I'll try it and let you know how it goes.

---

### Post by les-h on 2007-08-27
Have you managed to get it working yet?  I have it working but struggling with full screen mode.

---

### Post by Gidskid on 2009-04-29
I typ[CENTER]e[[LEFT][/LEFT]ed in all the commands but i still can't get the damn thing to open. Does it open like it does in windows or am i missing something?

---

### Post by archeryguru2000 on 2009-06-24
Has anybody been able to get this program to work with an actual game?  I've been able to get my commands from a game pad to emulate keyboard commands but only in specified windows, not in an actual game.  Any luck from anybody else?

~~archery~~

---

### Post by geniusguy2000 on 2010-05-05
mine has 

joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.3   Binary built on Dec 22 2009 at 13:45:44

Error opening /dev/input/js0!
Are you sure you have joystick support in your kernel?

---

### Post by mike5853 on 2010-09-11
I DO NOT uNDeRStAND...

I program robots, and this is much harder...

please somebody help

---

