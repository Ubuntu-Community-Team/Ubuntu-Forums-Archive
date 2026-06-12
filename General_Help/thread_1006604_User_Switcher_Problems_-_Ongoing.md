---
title: "User Switcher Problems - Ongoing"
date: 2008-12-09
forum: General Help
---

### Post by Sidney232 on 2008-12-09
Hi, I originally posted this problem in the absolute beginners forum but I'm posting here because I thought I might get a bit more specific information. You can see my original two threads by searching for ny user-name of course. Anyway to cut a long story short my original post was...

===============================================================
My wife is shouting about going back to Windows if I can't fix the FUSA in Ubuntu. I really don't want to do that as it's been a really good experience so far.

I recently upgraded from Hardy to Intrepid and everything appears to work just fine… all except the fast user switcher. It sometimes fails to work altogether. It sometimes throws up error messages such as:

Cannot start new display - there were errors trying to start the X server.

Or...

Graphical System Error - The graphical interface did not properly start, which is needed for graphical logins. It is likely that the X windows system or GDM is not properly configured.
Details - X server failed to finish starting. 3X failed.

From reading about on here I get the idea that the problem is related to my graphics card or its driver or is that just a red herring?

I’m running a Dell Dimension 4400 1.7GHz with 765MB Ram. Display is an old Scott LW851 LCD, video card is ATI Rage 128 Pro. There’s nothing else on the PC – no dual boot etc. I installed originally last year from 7.10 and upgraded to 8.04 with no problems. I have two HDD; a 13GB one on which Ubuntu is installed and a 40GB one set up just for data. Both work just fine.
===============================================================

I've just ordered some new memory to take me to 1GB to see if that helps anything on the off chance.

Next I might have to get a new video card although no one in the beginners forum could say for certain whether that really was the root of the problem; is it?

Also if I was to get a new card I can't work out that if the release notes for 8.10 say that r300 chips are not supported does that imply that r100 and r200 chip sets are not supported too? (I was looking at an ATI Radeon 7000 VE as it's cheap enough not to matter if it doesn't work and it looked like the newest one that my PC AGP power supply could handle (250W) but it's got an r100 chipset.)

Can anyone help with the above?

---

### Post by girishven on 2008-12-10
Have been having the same problem from the time I switched to Intrepid. Happens even with 2 gigs of RAM and a Nvidia 6800 card.
Switch user does not work most of the time. Quite annoying.
The problem should have to do with the nvidia restricted drivers not working well with the new XOrg. I believe that we need to wait for a fix. 

If you use the default ubuntu provided drivers ( not the restricted nvidia drivers ), this problem should not occur ( haven't tried it myself, but will do). The downside though is that you would not be able to realize the compiz effects.

---

### Post by girishven on 2008-12-10
Performing the steps below appears to have resolved the issue for me. I will however need to wait for a day or two to make sure that the problem has gone away entirely.  

sudo dpkg-reconfigure xserver-xorg to rewrite the xorg.conf. Creates a fresh xorg.conf.

Afterwards run sudo nvidia-xconfig assuming you are running nvidia drivers.. 

I now get an Nvidia splash screen when I try to switch users before getting the login screen. but thats OK.
I use the latest Nvidia beta drivers.

---

### Post by Sidney232 on 2008-12-10
Thanks.
I have no proprietary drivers in use on the system. I'm not too worried about special effects I just want to be able to switch users reliably.
Let me know how your fix gets on. I don't have an nvidia card (see my original post) so I'm not sure entering your fix will do a lot.
Sounds like I should resign myself to waiting for a fix...

---

