---
title: "HL2 not working, can't edit winecfg"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by Ludford on 2007-07-23
I can't seem to get HL2 working. I get to the loading screen but it just crashes while loading (the one directly before the main menu)

I read that I may need to configure wines sound, but when I try to access the sound tab in winecfg I get...

"fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack"

Any Ideas?

EDIT: I noticed that the audio tab comes up if you leave it for 5 min, I set up all the stuff like it says on winehq, but it still crashes.

Not working on linux not wokring on windows.... is there any OS this game will run on?

---

### Post by cogadh on 2007-07-23
Ignore that message, first off it is a "fixme", which is only a developer message, secondly, it only really applies if you are using the Jack audio system, which you are not.

After that message appears in the terminal, are you still able to access the Audio tab (it will be slow to load)?

---

### Post by Ludford on 2007-07-23
Yes I noticed it will load if I leave it open for about 5 min

I have set up all the stuff according to winehq, but it is still crashing.

I'm downloading direct x libraries to see if that helps.

Also what compatibility mode should I run in? XP?

EDIT: directX didn't help it still crashes.... this is weird it crashes when I run it on my windows boot aswell, but at loading screens that are between areas of the level

---

### Post by cogadh on 2007-07-23
What are your hardware specs (processor, video card, RAM, sound)?

Also, when you say you downloaded the DirectX libraries, you didn't try to install the DirectX runtime with Wine, did you?

---

### Post by Ludford on 2007-07-24
CPU: Intel core duo 1.6 x2

RAM: 2GB

GPU: Intel 945 GMA. 128mb

(It meets all the requirements I checked)

It's an advent 7111 laptop if that helps.

and I installed whatever the directX thing was in wine doors

---

### Post by cogadh on 2007-07-24
I wasn't really concerned about requirements, when you said the same thing happens in Windows, I was curious about something in your hardware that might be the source of the problem on both systems. I know many older games will have problems with the dual core processors, which can usually be solved by assigning the applicatin to a single core, but I don't know how you would do that with Wine/Ubuntu.

One question though, what driver are you using for that Intel GPU? I know that many people have issues with the Intel drivers, that could be the cause of your issues in Linux at least.

On a side note, you probably shouldn't use Wine-Doors. It's still alpha software and has some significant bugs in it. I'm not sure what it installs for DX libraries, but there are only a handful of DX libraries that won't screw up Wine completely.

EDIT - I just remembered we discussed Wine-Doors and HL2 in a [different thread]("http://ubuntuforums.org/showthread.php?t=507859")before. Have you already gone through the Wine AppDB page I posted in that thread and made the necessary winecfg/regedit changes required to get HL2 running?

---

### Post by Ludford on 2007-07-24
Yes, the first thing I did was do all the things it says on Winehq.

The driver I am using is i810.

I'm begining to think i have a dud copy of HL2 becuase it won't run on my desktop either (I don't have a disk, I was given a CD key by my uncle since he doesn't use the account anymore)

---

### Post by jacob01 on 2007-07-24
are you using steam

---

### Post by Ludford on 2007-07-25
Obviously, I was given a steam account.

---

