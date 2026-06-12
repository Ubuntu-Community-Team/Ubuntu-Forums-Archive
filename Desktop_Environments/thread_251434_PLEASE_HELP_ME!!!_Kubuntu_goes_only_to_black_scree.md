---
title: "PLEASE HELP ME!!! Kubuntu goes only to black screen with the word kubuntu &amp; blue bar"
date: 2006-09-05
forum: Desktop Environments
---

### Post by TommyMann on 2006-09-05
Ok, so here is my story...

(I'm a little wet behind the ears at Linux)

I'm on a gateway 6510gz laptop. I have an intel graphics card.

My screen was looking distorted so I went to fix the resolution.

I opened up terminal, I tried the steps on the the howto correct resolution help.

First I got a thing about no such file xorg.conf, so someone had me put some code into terminal that reinstalled/repaired/whatever.

Then I return to the howto.

I open xorg.conf with Kate.

Sorry I can't be more specific, but for the life of me, I can't find the guide on help.ubuntu.com, it was linked to me in the kubuntu irc, which I can't get back on without my computer becaue I know nothing about IRC.

I changed the settings for "display" to 1280x800.

And then I hit alt-ctrl-backspace like it said.

And now I have the cold stare of kubuntu looking down at me in the abyss like darkness dividing himself from me with his blue bar of agony.

All I wanted was the correct resolution. I've been trying to get help, but people just keep sending me to links that have gotten me further behind than forward because they don't talk you through little errors.

If I could get some serious help, that would be great.

---

### Post by tatimmer on 2006-09-05
Sorry, but my advice comes cheep.

My only suggestion is that you boot into safe mode (non-graphical root login) and hopefully you know how to use a non-graphical text editor like vi.  Looks like your xorg.conf may need some tweeking.  May need to get onto the internet from another computer and download some info on how to hand tweek xorg.conf to some default safe setup.  Good luck.

---

### Post by TommyMann on 2006-09-05
I really need someone with exceptional linux experience who can walk me through this.

---

### Post by TommyMann on 2006-09-05
I refuse to let this pass. I need help, and I need it from those with some experience with Linux. Maybe even form the moderators. I read that ubuntu has great support, and that's why I got it, but right now I feel ignored like I'm on a petty windows help line. Seriously, can someone help me.

I'm not letting this go. I'll keep replying to myself to get it back into vision on the first page. I'm not slipping through the cracks when my computer won't WORK!

Please, for the love of bog, assist me!

---

### Post by someguyouknow on 2006-09-05
boot in safe mode and type startx
if there is something wrong with your xorg.conf, it will usually tell you what line it is. you probably just missed something minor.

either that or do a sudo dpkg-reconfigure xserver-xorg 
then change the resolution via system settings.


oh and i am not an expert at all but... I have had to do this many times.  that screen doesnt even scare me anymore;)

---

### Post by TommyMann on 2006-09-05
Thanks, but when I boot in recovery mode (there's no option for safe mode), I get root@tommymann-laptop:~#

---

### Post by someguyouknow on 2006-09-05
safe mode = recovery mode
in recovery mode, you dont have X unless you start it.

thats looks right.
there, type startx
if it doesnt start up, near the end it should have what line is messed up.
then you can do a edit that part of your xorg.conf file.

or you can just type dpkg-reconfigure xserver-xorg
there you can reconfigure it and along the way you can set the resolutions you can use.

---

### Post by TommyMann on 2006-09-05
the error says no screens found

---

### Post by TommyMann on 2006-09-05
Thanks for your help, it's running again, but it still has my resolution messed up

Any advice?

---

### Post by brucevangeorge on 2006-09-05
[FONT="Arial"]This should help.[/FONT]

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

