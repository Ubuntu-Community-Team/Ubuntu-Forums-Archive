---
title: "Gutsy installation issues with Dell CRT monitor and nvidia 8800GT"
date: 2008-01-14
forum: Desktop Environments
---

### Post by imjustsomeguy72 on 2008-01-14
Ok. I recently built a new machine with an 8800GT, and cobbled it together with a CRT Dell Trinitron. I'm trying to get a dual boot between Vista (only for DX10) and Gutsy going, but I'm having problems installing Ubuntu.

I can get to the first menu with the options for standard live environment, safe graphics mode, memtest etc. When I pick the first option, it loads up with the bar thing, and then thinks for a bit, and then comes up with a prompt telling me that it can't detect either my monitor or gpu, and suggesting i run in low graphics mode. The trinitron doesn't appear in the list, but picking another monitor with the same native res and refresh rate, and then picking the nv driver, doesn't help. Neither does running in low graphics mode. After selecting low graphics mode from that prompt, it then comes up with the screen with the loading start-up scripts (/etc/init.rd) and then hangs, with no command prompt or anything.

Picking safe graphics mode from the first menu ends with similar results, except that it renders the x desktop for about half a second, before crashing and then trying again. It does this about six times, before a prompt comes up, telling me that its crashed 6 times :P Then it hangs at the aforementioned screen again.

I believe X is crashing, and probably the best solution would be the alternate CD. But I'd rather not have to go and download yet ANOTHER iso, so if somone could offer a solution, it would be much appreciated :D

---

### Post by TeaSwigger on 2008-01-14
I understand not wanting to grab the alt iso after grabbing the live CD, but it looks like you'll have to, unless someone happens to have the same monitor etc and happens to read this and reply. To best those highly unlikely odds, please post the actual model of the monitor here.

Alternately, ;) there are two other things:

- The CD is defective. It has to be well neigh perfect to install / run an OS. Run the self test on the CD to verify it. If still in doubt, burn another one, at low speeds, and be sure to test it too. Then maybe try the alternate install CD.

- Searching the web for the specs of your exact monitor might be handy if you don't have any luck otherwise - to edit your own /etc/X11/xorg.conf file prior to starting X. That's out of my depth I'm afraid. 

Good luck :)

---

### Post by imjustsomeguy72 on 2008-01-19
UPDATE: The monitor DOES appear in the list, but selecting it and the nv driver made no difference.

I'm usiong a dvi to vga adapter from my graphics card, if that makes any difference.

I tried starting x from the virtual terminal thing, and I got a "no devices detected" message.

monitor is a Dell P70 Trinitron, native res 1024x768 @ 85hz. Graphics card is an 8800GT 512mb.

---

### Post by MichiganMan on 2008-01-19
Be aware that the nvidia driver in Gutsy doesn't support 8800GT's.  This may be the crux of most of your problems, although I would think that you could run in low graphics by choosing nv and a generic monitor...  What you're describing, the restarting six times over, crashing after rv.local, sounds like what I went through yesterday after the xorg update made it so that I could only boot into failsafe Gnome.  Reinstalling the latests Nvidia driver solved that.  

Go here:  [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

You'll read alot about the latest nvidia driver and 8800GT's.  Be aware that there is a bug in 169.07 that causes the 8800GT's fan to run at 100%.  It can be fixed installing the latest nvclock, which allows you control of the fan.  The bug has been identified and nvidia is working on it.  I'm running the beta driver 169.04 on my 8800GT, and it runs like a dream.  I would advise installing that for 8800GT's until Nvidia gets a fixed driver out.  

Hope you find something in here that helps.

---

