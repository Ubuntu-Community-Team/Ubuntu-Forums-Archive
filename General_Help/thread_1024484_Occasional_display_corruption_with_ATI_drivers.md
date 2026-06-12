---
title: "Occasional display corruption with ATI drivers"
date: 2008-12-29
forum: General Help
---

### Post by tekai on 2008-12-29
Hi.

Sorry - first time poster.

I'm running Intrepid with an ATI HD3850 card with proprietary drivers (from repository) with compiz disabled.  

Occasionally my display will become corrupted.  It looks like the display is broken into columns of I'm guessing 32 or 64 pixels wide, and a random selection of lines from each column seems to be shifted elsewhere.  I've attached a couple of screenshots as a picture's worth a 1000 words :-)

I've seen it happen rarely while viewing images in Firefox or doing other graphic intensive activities, and can  get it to happen while playing a game with Wine.  Using Wine, I'd say it happens 25% of the time, but usually not until after an hour or two of play.  I don't think it's Wine specific as I have seen it happen without ever launching Wine for that session.

If I play a video while the display is corrupted, the video is fine, but the rest of the display is still garbled.  

If I enable desktop effects, the screen is rendered clearly, but the mouse pointer is off by a few pixels.  Best example is when the pointer is over the close icon (the little X) and I click, it actually clicks the minimize icon instead.  There is also a couple of random pixels near the mouse pointer that follow it around.

Tried logging out and restarting the X server using Ctrl-Alt-Bksp, but neither fixed the problem.  Funny enough, the login screen was fine.  

Restart the computer and things are fine.

I don't see anything in /var/log in any of the log files either.

Suggestions or any information that I can gather?

Thanks!
Greg

---

### Post by tekai on 2008-12-29
It just happened again just after I posted the original message, which I posted just after a reboot from when it happened earlier tonight.  

I've switched to using compiz for now so I can see my screen at least and won't reboot for a day or so in hopes someone has suggestions.  It's now just annoying that the mouse is off a bit so have to be careful on what I click :-)

---

