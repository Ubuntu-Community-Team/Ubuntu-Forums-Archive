---
title: "ZSNES (super nintendo emulator) comes up for half a second and disappears."
date: 2008-04-19
forum: Gaming &amp; Leisure
---

### Post by thegreatdestroyer on 2008-04-19
I installed it using add/remove. Before that I had downloaded it from the homepage and tried following the instructions for installing it. But I got a configure error saying something like C cannot build an executable. So I trashed the folder I had ZSNES in and used add/remove to install. It installed, but when I click its icon in Applications > Games > zsnes it comes up for half a second and disappears. Can someone help me figure this out? I'm using Ubuntu 7.10 and I believe ZSNES 1.51 if that's the version add/remove installed.

---

### Post by prshah on 2008-04-19
> **thegreatdestroyer said:**
> when I click its icon in Applications > Games > zsnes it comes up for half a second and disappears. 

open a terminal (Applications-Accessories), then type in ```
zsnes
``` and post error messages if any.

---

### Post by thegreatdestroyer on 2008-04-19
OK I did what you said and this is from the terminal:

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/thegreatdestroyer/.kde/socket-TheCesspool.
can't create mcop directory

---

### Post by thegreatdestroyer on 2008-04-19
Oh I should add that I'm using the gnome desktop and the last message in terminal said it was creating a link for kde. Don't know if this is a problem. Also I uninstalled 1.51 and installed the version that came just before it and came up no problems. But I uninstalled it and reinstalled 1.51 cause I wanna use the latest version if I can. I didn't try playing games with the version before 1.51 though.

---

### Post by jjk7288 on 2008-04-19
Create the directory .kde/socket-TheCesspool in your home directory and it should work.

---

### Post by mastahkillah666 on 2008-04-21
Or you can follow [[COLOR="Red"]**THIS LINK**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=593888") to find an alternative solution to your problem.

Be sure to read the whole thread in order to understand the mechanism behind the error.  Hope this helps.

See ya around the forums.

---

### Post by thegreatdestroyer on 2008-04-21
jjk7288 your tip solved the problem. Thanks man. I need a little more help though. The sound is choppy and I've reduced the sampling rate which helps a little. I'm sure it's not my soundcard as I've read some articles and it seems many people are having sound issues with version 1.51. One guy said he was having issues very similar to mine and enabled libao as an alternative to SDL for sound. Said to check zsnes --help and see -ad flag. I'm not sure if this would help me or not. Anyways I'll be making another post including my system specs.

---

