---
title: "Open Office resets me to login screen randomly"
date: 2009-06-15
forum: General Help
---

### Post by gennoveus on 2009-06-15
Hello,

I couldn't find any previous mention of this error anywhere else. Please help me! Also, I apologise in advance if I've put this post in the wrong place or if I've given not enough or irrelevant information (I'm relatively new to Ubuntu/easy peasy).

Whenever I use open office, there seems to be a random chance that it crashes. Sometimes it doesn't. Sometimes it will crash when starting up, but sometimes it will crash after using it for an hour. I have no idea how to replicate the error. Earlier today it even happened when I was AFK. When I say "crash," I mean that it randomly resets to the login screen.

I'm actually using easy peasy 1.1. Here are my specs:

release 8.1 intrepid
kernel linux 2.6.27-8-eeepc
gnome 2.24.1

its an eeepc 701 (4gb solid state drive one)

I know this is probably not enough information. Does anyone have any ideas on how I can get some more information to pinpoint the source of the problem? I need to do a lot of work and and this is slowing me down. 

Please help!

Thank you

---

### Post by gennoveus on 2009-06-15
Bump

---

### Post by Dreamlocked on 2009-06-15
Have you tried disabling special 3D effects?

---

### Post by gennoveus on 2009-06-15
Thanks for the response.

Where do I change that setting? I disabled "use hardware acceleration" in the options in Open Office.

Unless you are talking about the visual effects options where you change the appearance of Ubuntu (sorry, I'm not running Ubuntu in English so I don't know the English name for the option. I mean one of the tabs in the same area where you can change the background image etc)

I turned all the effects off in there too, but it still crashes.

I'm not sure if it has anything to do with performance. I was trying to replicate the error so I opened 20 or 30 files at once for about 10 minutes and it didn't crash, but just a moment ago it crashed when I only had one open after about 30 seconds.

Anyway, I've found the crash is only caused by Word Processor and not Spreadsheet or Presentation.  

Any input is appreciated!

---

### Post by gennoveus on 2009-06-17
No help eh? 

Well I figured it out myself. It only happens when open office and rythmbox are open at the same time. It could have something to so with ALSA. I stopped using ALSA and rythmbox and the problem is gone.

I'll post the exact cause of the problem when I can be ****** testing it.

---

### Post by aesis05401 on 2009-06-17
Hi, 

Randomly resetting to the logon screen is often related to a problem with X server.  

Unfortunately, I have no idea why your particular combination of conditions is running into issues.  

If you are only seeing this issue when you put the machine under heavy load, then you may be hitting some sort of resource issue resulting in X restarting.  

Sorry I can't be of more help.

---

### Post by gennoveus on 2009-06-17
Hi Aesis,

I don't think it has anything to do with load. I stress tested it by opening about 40 different large files in office, as well as a lot of pdfs etc. It didn't crash, even after 30 minutes, but during another session it crashed when only one document and rythmbox was running after about 1 minute.

I ran top in the terminal and it didn't seem to be under too much stress.

It's very odd. Anyway, I found a work-around so at least I can get my work done.

---

