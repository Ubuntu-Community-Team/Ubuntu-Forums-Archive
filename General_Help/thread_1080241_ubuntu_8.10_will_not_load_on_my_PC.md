---
title: "ubuntu 8.10 will not load on my PC"
date: 2009-02-25
forum: General Help
---

### Post by ashpuk on 2009-02-25
Hi all, (sorry for long post but trying to be detailed!)

I am new to the world of Linux (but pretty experienced PC/Mac user) and thought I would give it a go with Ubuntu 8.1. 

I have downloaded the .iso from the website and burnt it to a CD. I have then tried to run the live CD on my PC (currently running XP Pro) just to give Ubuntu a go and see what its like. The splash screen comes on as it is supposed to with the orange bar moving from side to side and then it loads as it is ment to (orange bar turns to a progress bar). Once the loading gets to 100% the screen goes blank as if it is about to show the Ubuntu desktop. But thats all I get, either a blank screen or a black screen with a flashing cursor.

I have tried loading into safe graphics mode & also watched it startup without the splash screen but am pretty sure I saw no errors.

Before everyone asks me if I have burnt the cd at slowest speed, I have also tried the same CD on my Macbook Pro and it ran perfectly (several times). Its now just annoying me because I want to get it running on my PC!

I have searched the forums but cannot really find an answer to my problem :-(  

Specs of PC are (not the best, but should be OK?):

Celeron 2.6Ghz
1GB Ram
Intel 82865G Graphics Chipset (onboard)
80Gig HDD (about 20Gig Free)

Just wondering if anyone has any more tips about what may be causing the problem? Thanks in advance..

Cheers Chaps!

---

### Post by Radioman991 on 2009-02-25
My 0.02

Can't really tell you EXACTLY what's happening, but you might try downloading the alternate install CD.  It isn't pretty...kind of looks like an old DOS screen..but in color.

If it gets as far as it did, and the CD functions flawlessly on another machine, I would suspect a graphics issue, and the alternative installer might get you around that to get the system installed.

YMMV

PK

---

### Post by ashpuk on 2009-02-25
Thanks mate, quick question:-

Can I run it live (off the cd) or will I have to make the install?

I am actually trying to do this on my office PC and do not want the hassle of partitioning the PC and going through the install if it may not work- thats why I want to go down the Live CD route if poss! 

thanks

---

### Post by avtolle on 2009-02-25
The alternate CD will not allow you to run in a Live mode; it is for installation only. Sounds like your Intel graphics is the problem to me. I don't have the link at my fingertips, but you should take a look at the release notes for 8.10 for an explanation (it has something to do with the driver for the Intel graphics set and desktop effects, a/k/a Compiz not being supported) and work around. One  suggestion I have is to try 8.04.2, which is a LTS (long term support) release and see if it can load without the graphics problem.

---

### Post by ashpuk on 2009-02-25
OK..so I dont have any blank CD's lying around and I got bored so I went for the Wubi (?) Windows installation thingy (so i did not have to partition the drives etc) which seemed to work OK.

If I try and boot Ubuntu normally it loads OK (as per the original post) and actually displays the mouse cursor on a black screen & then hangs.

However, if I now run it in safe graphics mode it shows the mouse cursor & the background, but then hangs, so it does look like it may be an issue with the graphics, but at least I am making progress..

I have checked through the release notes and there was no mention of my graphics card on there and I have checked the forums and it does not appear as if anyone else seems to have this problem (or noone else has this graphics card lol). 

Next question - is there any way that I can load Ubuntu in say an even more basic graphics mode than safe graphics mode to allow me to get the thing running & sort it from there?

Or

Am I wasting my time with this and really the only answer is either; a new graphics card supported by linux, or try running an older version and if that works settle with that?

Obviously it would be nice to try and get Ubuntu 8.1 running without a new graphics card but any thoughts would be apprecaited

thanks in anticipation

---

