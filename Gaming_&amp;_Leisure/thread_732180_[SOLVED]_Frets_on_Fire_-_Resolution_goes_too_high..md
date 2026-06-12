---
title: "[SOLVED] Frets on Fire - Resolution goes too high...or low..."
date: 2008-03-22
forum: Gaming &amp; Leisure
---

### Post by nachomania on 2008-03-22
Hello. I've installed Frets on Fire through the terminal, and everything went fine. The problem is, (or at least I think it is), that the game's resolution is too high for my monitor. I can hear music when I run the game, but my monitor bars the signal, and gives me the warning screen. Any way I can lower this, or find out what's causing it?

---

### Post by tobiasgideon on 2008-03-23
> **nachomania said:**
> Hello. I've installed Frets on Fire through the terminal, and everything went fine. The problem is, (or at least I think it is), that the game's resolution is too high for my monitor. I can hear music when I run the game, but my monitor bars the signal, and gives me the warning screen. Any way I can lower this, or find out what's causing it?

I get a similar error too! I hear music for the 1st few seconds then I get a message saying **_Video Mode Not Supported!_** I cant seem to find anything in Google!!!!

have you tried running it in the terminal with the -v option so that you can see what the console says?

If I find any other ideas I'll post them.

I am running Ubuntu 7.10 - Gutsy with an Nvidia Geforce 6600LE with the latest drivers installed via the Envy system!

---

### Post by nachomania on 2008-03-23
```
kaipraths@kaipraths-desktop:~$ fretsonfire -v
(W) PyOGG not found. OGG files will be fully decoded prior to playing; expect absurd memory usage.
(W) PyAmanith not found, SVG support disabled.
(D) Initializing audio.
(D) Audio configuration: (44100, -16, 1)
(D) Initializing video.
(W) Video setup failed. Trying without antialiasing.
(D) Enabling high priority timer.
(D) 0 joysticks found.
```

There's more, but it's about loading stuff for the menu. 
Oh...I seem to be missing some stuff. If anyone has gotten them in, please tell. I'll try to find them...

---

### Post by nachomania on 2008-03-23
Well, I've found (from google) the stuff it said I was missing. Pyamanith and PyOGG. Now, if only I knew how to compile :)

---

### Post by nachomania on 2008-03-23
sudo apt-get install python-pyvorbis python-pysqlite2 python-mutagen python-pyogg python-elementtree

Installed PyOGG

---

### Post by tobiasgideon on 2008-03-23
I managed to solve my problem!!!!!

This might help you.

You need to make sure a file exists in /home/Username/.fretsonfire

this is a hidden directory, it must contain a file called

fretsonfire.ini

I didnt have one so it couldn't initialise properly

if you create a blank file and paste the below code into it, it might work!

> [engine]
highpriority = True
tickrate = 1.0

[opengl]
svgquality = 1
supportfbo = False
svgshaders = False

[theme]
base_color = #FFFF80
fret3_color = #3333FF
background_color = #330000
fret0_color = #22FF22
fret4_color = #FF22FF
selected_color = #FFBF00
fret1_color = #FF2222
fret2_color = #FFFF22

[player]
key_action1 = K_RETURN
key_action2 = K_RSHIFT
name = Dragu
key_4 = 285
key_up = K_UP
key_1 = 282
key_right = K_RIGHT
key_5 = 286
difficulty = 0
key_left = K_LEFT
key_cancel = K_ESCAPE
key_3 = 284
key_2 = 283
key_down = K_DOWN

[game]
selected_song = Sweet Child
language = English
selected_library = songs
uploadurl = [http://kempele.fi/~skyostil/python/fretsonfire/upload](http://kempele.fi/~skyostil/python/fretsonfire/upload)
leftymode = False
tapping = True
uploadscores = False

[video]
fullscreen = True
multisamples = 4
fontscale = 1.0
fps = 80
resolution = 1024x768

[audio]
stereo = True
screwupvol = 0.25
bits = 16
delay = 100
rhythmvol = 1.0
frequency = 44100
buffersize = 2048
guitarvol = 1.0
songvol = 1.0


Hope this helps!
It rocks dude!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:guitar:

---

### Post by nachomania on 2008-03-23
It worked! Thanks a ton!

---

