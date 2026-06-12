---
title: "Is there a version of Ubuntu that works best for gaming?"
date: 2008-08-16
forum: Gaming &amp; Leisure
---

### Post by herteljt on 2008-08-16
A few months ago I bought Guild Wars and tried to get it running on Ubuntu 8.04.  After reading many different threads and all the suggestions on winehq.com I decided that the easiest solution was to install a different version Ubuntu (I went to 7.10) on a separate partition.  

When I first started using Ubuntu I had issues getting games like Nexiuz to work properly.  I found that some of these issues went away with different versions (of course others always pop up :) ).

This has gotten me to thinking, is there a version of Ubuntu that has been more compatible for games (and I know the word game is a little vague) than others?  What version are you running?

---

### Post by olejorgen on 2008-08-16
I think most games will run better if you turn of "Desktop effects" first.

---

### Post by herteljt on 2008-08-17
> **olejorgen said:**
> I think most games will run better if you turn of "Desktop effects" first.

I have also found this to be true.  If I enable desktop effects then compiz takes over direct rendering (which is to say I lose direct rendering).  

This may be specific to my video card (Radeon 9600) or ati cards in general.  I was just wondering if anyone has had a great deal of success with one particular version of Ubuntu.

---

### Post by Frem on 2008-08-17
Yeah, Compiz is an issue right now. I use Compiz-Switch to toggle it on and off when I play games (though the website seems to be down right now). In future versions of Ubuntu, this is likely to be less of a problem, as DRI2 will allow applications that need direct rendering to have it -- or something like that; I don't really understand how it works.

All versions of Ubuntu are based off the same core and should have similar hardware compatibility. In the past, the ATi drivers have been netorious for having much better performance and fewer rendering issues in Windows; I'm not sure if this is true for your card or not.

So, no, not really. The drivers are what is really going to make the biggest difference, and the individual software packages in each Ubuntu variant's release can be installed in any of them (For example, "aptitude install xubuntu-desktop" will install the packages comprising Xubuntu).

---

### Post by anjilslaire on 2008-08-17
Your video drivers and wine version/configuration will be a bigger issue than what version of Ubuntu you're running.

---

### Post by chiefgeargrinder on 2008-08-17
> **herteljt said:**
> A few months ago I bought Guild Wars and tried to get it running on Ubuntu 8.04.  After reading many different threads and all the suggestions on winehq.com I decided that the easiest solution was to install a different version Ubuntu (I went to 7.10) on a separate partition.  

When I first started using Ubuntu I had issues getting games like Nexiuz to work properly.  I found that some of these issues went away with different versions (of course others always pop up :) ).

This has gotten me to thinking, is there a version of Ubuntu that has been more compatible for games (and I know the word game is a little vague) than others?  What version are you running?

I think for gaming your better keep your dual boot. as im finding out wine is just about worthless.if you get the game to work expect about 25fps. then when you want to uninstall the game you have icons left that you cant remove.cedega will just take your money and run and just works about as good as wine. I have a pretty good system quad core 2 8800gt video cards and steam yes does work with wine and ccs and half life 2 but with dismal performance.

---

### Post by Brebs on 2008-08-17
> **chiefgeargrinder said:**
> then when you want to uninstall the game you have icons left that you can't remove.
They can be removed, you just need to know where they are - probably ~/.local/share/applications/wine/Programs/

---

### Post by Vitamin-Carrot on 2008-08-18
tbh I have never had an issue witht he desktop effects when playing ut2k4 ... I have never needed to turn them off ...

If turning them off is your best bet i think you can have a compiz button that easily allows you to do so ...

I havent touched my home machine in weeks so yeah ive been a bit busy ...

hno doubt i will have mega updates watiing me when i finally manage to get some time to myself

:lolflag:

---

