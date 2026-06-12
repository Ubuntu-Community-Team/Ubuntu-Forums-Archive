---
title: "Gutsy 7.10 install error Inspiron e1505"
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by Adar on 2007-12-13
I am just trying out Ubuntu after not using any flavor of linux in about 10 years.  My machine is an Inspiron e1505 with the ATI Mobility Radeon x1400 video card.  I have been completely unsuccessful getting it installed, although my problem IS listed in the forums.

Basically, I boot from the 7.10 CD.  I choose to install, and it happily moves to the next screen, lots of info scrolls by as all the scripts are run, and then, I end up with the following error:

Microcode "bcm43xx_microcode5.fw" not available or load failed.

After a little while, a blue screen comes up telling me that the video system has restarted more than 6 times in 90 seconds.  

Now, I did some googling, as well as searching on these forums directly.  This specific problem appears to be related to the 1390 wireless card.  OK, fine.  However, the fixes for this involve being able to be in the system, or be able to get to the console.  CTRL-ALT-F1 at any point does not give me a console.  

Is there some boot option I can add so that it DOESN"T load into the GUI, and just leaves me at my command prompt, and possibly be able to fix this?  I have seen a number of posts where people using this same model said they had no problems installing it.

Oh, and while I was experimenting, I also tried 7.04 Feisty Fawn and 8.04 Hardy Heron.  7.04 just freezes on the loading screen, no errors or anything, just a plain black screen.  8.04 DOES actually install, but finding any drivers or anything for it is next to impossible.  I mean, the system itself DOES work, but I can't install the correct ATI drivers, because they don't exist (at least not where I found all the other drivers).

Anyone have any bright ideas on what I can do to get either 7.04 or 7.10 working?  I'd prefer to stay away from the 8.04 since it isn't the stable build.

Keep in mind, although I am not a computer illiterate, it has been 10+ years since I have done anything with Linux.

---

### Post by Paul S on 2007-12-14
If you install via the alternate cd, then it does not matter that X can't / won't start.  You'll be able to boot into the recovery console and play with your ATI drivers and xorg.conf to work the bugs out, and eventually will find something workable.  The ATI card is your biggest problem, I think.  You might be able to get a "vesa" driver to work initially, so you can at least use the gui while you're trying different ATI drivers.  Also, AMD will be releasing a newer (perhaps better) fglrx by month end .. check their website as well as phoronix.com for howto's.

Regarding the wifi, if the open source drivers don't work, you should be able to get it going with ndiswrapper.

HTH,

---

### Post by Adar on 2007-12-14
> **Paul S said:**
> If you install via the alternate cd, then it does not matter that X can't / won't start.  You'll be able to boot into the recovery console and play with your ATI drivers and xorg.conf to work the bugs out, and eventually will find something workable.  The ATI card is your biggest problem, I think.  You might be able to get a "vesa" driver to work initially, so you can at least use the gui while you're trying different ATI drivers.  Also, AMD will be releasing a newer (perhaps better) fglrx by month end .. check their website as well as phoronix.com for howto's.

Regarding the wifi, if the open source drivers don't work, you should be able to get it going with ndiswrapper.

HTH,

Well, I made it a bit further.  Instead of using the CD version, I downloaded the DVD version of Kubuntu.  I also disabled the wireless card in the BIOS.  This stopped the stupid microcode error from coming up.  I would get the beginnings of the GUI, a light blue background and an actual mouse cursor that moved.  Then it would drop back to the console.  I will have to try it again, because I didn't write down the message.  Something about my display doesn't support DVI, except it wasn't DVI in the message.

Unfortunately, being such a newbie with this stuff, I am spending a large portion of my time on google and the ubuntu wiki looking for how to do things.  For example, I know what and where the xorg.conf is, and can edit it, but trying to figure out manually what to put in there to get it running is beyond me right now.  Hopefully I will have more time to play with it tomorrow.  

Oh yes, and I had to use the text based installer.  The system works just fine, but no GUI, only console.  Can't start up the GUI.  I tried running startx (which gave me the error about my display) and kdm.  Then I even installed gdm and tried that too.  none of them worked.  

From all the searching on google, I have found that ATI does seem to be more problematic. :)  Oh well, it is an adventure.

---

