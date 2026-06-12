---
title: "Firefox w/Flash is *so* unstable!"
date: 2006-08-30
forum: Desktop Environments
---

### Post by billycub on 2006-08-30
I have at least three pretty standard PC's w/Ubuntu Dapper 6.06.1 that are all exhibiting the same problem:

Firefox, installed with the non-free Flash plugin, hangs very frequently after watching Flash animations/videos.  Particularly problematic are popular pages w/Flash such as YouTube, JayIsGames, etc.

The browser will sometimes play the video and then become unresponsive; other times it will hang while loading the page.  Either way, I have to use the window manager to Force Quit the browser.

The problem is so frequent and annoying that my friends who I'm trying to convert to Ubuntu are on the verge of going back to the dark side.  So:

1) Is this a well-known problem?  I've searched these forums and have found many references to Flash not playing sound, or to Flash 8/9 not being supported, but I don't see anything re: instability.

2) Any known solution or suggestions?  I'm quite adept at Ubuntu; not a newbie at all, so I'm not afraid to get my hands dirty.

Main system specs:
- HP Pavilion A350Y Desktop (2.4Ghz Pentium 4, 1Gig RAM)
- Nvidia GeForce 7800GS (PCI), with 3d nvidia drivers installed

Thanks all! Any help appreciated.
-Billy

---

### Post by tagra123 on 2006-08-30
Have you tried starting firefox from the command line to see if its reporting any messages to the shell?

Could a library file be missing? 

Reinstall the problem programs ?

I haven't had any problems I can think of viewing flash or java pages.

Swiftfox gave me some problems just as you described, but the stable version of firefox works great for me.

---

### Post by ralphmerridew on 2006-08-30
A few days ago, I edited /etc/firefox/firefoxrc to change FIREFOX_DSP from "none" to "aoss".  Today I noticed a sudden reduction in stability.

Do the following:
1)  Open up google talk.
2)  Tell the person to send you a message in 30 seconds.
3)  Switch to a different tab.
4)  Wait.

I would hear the chime of receiving a message, and then firefox would lock.  I'm going to change it back to "none"; I dislike the occasional loss of sound, but that's worse than the stability loss.

---

### Post by mindseye1 on 2006-08-30
I thought I was going crazy, but this is the EXACT same behavior my Firefox is exhibiting! I was about to make a post with some lofty claim about the gmail chat box beep being the cause of my Firefox lock ups, but now I feel like it's not such a crazy observation after all! So the bad news is that I too am looking for a solution to this. The good news is you're not alone!

> **ralphmerridew said:**
> A few days ago, I edited /etc/firefox/firefoxrc to change FIREFOX_DSP from "none" to "aoss".  Today I noticed a sudden reduction in stability.

Do the following:
1)  Open up google talk.
2)  Tell the person to send you a message in 30 seconds.
3)  Switch to a different tab.
4)  Wait.

I would hear the chime of receiving a message, and then firefox would lock.  I'm going to change it back to "none"; I dislike the occasional loss of sound, but that's worse than the stability loss.

---

### Post by ralphmerridew on 2006-08-31
What does your /etc/firefox/firefoxrc file contain?

---

### Post by mindseye1 on 2006-08-31
Mine is set to use 'aoss', but it sounds like if I leave it blank the problems will go away. Although this will leave me with issues on flash videos with sound. Ugh, I guess I'd rather have stability though.

---

### Post by missmoondog on 2006-08-31
yep, got here searching for unstable firefox flash. instantly locks the browser tighter than a drum. don't mind to much. hate firefox anyway. was just playing with it. now i remember one of the reasons i hate it! ;)
flash is working in epiphany, opera, galeon, and konqueror.

easy fix. don't use it!! :)

---

### Post by TheNewGuy on 2006-08-31
> **billycub said:**
> I have at least three pretty standard PC's w/Ubuntu Dapper 6.06.1 that are all exhibiting the same problem:

Firefox, installed with the non-free Flash plugin, hangs very frequently after watching Flash animations/videos.  Particularly problematic are popular pages w/Flash such as YouTube, JayIsGames, etc.

The browser will sometimes play the video and then become unresponsive; other times it will hang while loading the page.  Either way, I have to use the window manager to Force Quit the browser.

The problem is so frequent and annoying that my friends who I'm trying to convert to Ubuntu are on the verge of going back to the dark side.  So:

1) Is this a well-known problem?  I've searched these forums and have found many references to Flash not playing sound, or to Flash 8/9 not being supported, but I don't see anything re: instability.

2) Any known solution or suggestions?  I'm quite adept at Ubuntu; not a newbie at all, so I'm not afraid to get my hands dirty.

Main system specs:
- HP Pavilion A350Y Desktop (2.4Ghz Pentium 4, 1Gig RAM)
- Nvidia GeForce 7800GS (PCI), with 3d nvidia drivers installed

Thanks all! Any help appreciated.
-Billy

To answer your question. Yes it is unstable, and adobe says they are working on version 9 for linux there's been alot of writeups on digg lately about it.

---

### Post by RSL on 2006-09-01
So _that_ is why my browser kept hanging up in Gmail's chat. I figured it was Flash but couldn't discern what exactly.

---

### Post by Uncle Spellbinder on 2006-09-01
> **missmoondog said:**
> yep, got here searching for unstable firefox flash. instantly locks the browser tighter than a drum. don't mind to much. hate firefox anyway. was just playing with it. now i remember one of the reasons i hate it! ;)
flash is working in epiphany, opera, galeon, and konqueror.

easy fix. don't use it!! :)

Been using Firefox for years. The past 6 months with Ubuntu. Working perfectly for me. NO flash problems what so ever (except for a few Flash 9 sites).

---

### Post by doobit on 2006-09-01
> **Uncle Spellbinder said:**
> Been using Firefox for years. The past 6 months with Ubuntu. Working perfectly for me. NO flash problems what so ever (except for a few Flash 9 sites).

Same here. No problems with Flash 7, but I've written to Adobe about giving us a Flash 9 because I need it for some online courses I'm taking.

---

