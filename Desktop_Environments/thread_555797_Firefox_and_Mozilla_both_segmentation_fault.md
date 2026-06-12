---
title: "Firefox and Mozilla both segmentation fault"
date: 2007-09-20
forum: Desktop Environments
---

### Post by ender42 on 2007-09-20
Both of them seg fault when I try to run them.

I'd basically been using Mozilla, because Firefox was a piece of crap.

But now I've got them segfaulting, and I uninstalled and reinstalled them, usually I was able to get a week or two of use out of each that way, but no luck this time.

I went into the other users, and closed out their Mozilla instances (which hadn't disappeared when I uninstalled it).

Tried again, no luck.

Finally got Galeon installed, and that's what I'm using currently.   Not what I'd like, especially as I wanted to browse my history and stuff.

Was going to try 'browser-history' application to try and keep track of stuff, but I don't think it works for Galeon - mostly firefox/mozilla and a couple others which I couldn't find to install.

Tons of trouble with this 'stable' LTS instance of Debian.  As soon as I can find an install disc for Warty, I'm moving backwards, so that I can have my USB ports back.  ****, maybe I  should just be running everything off of the live disc, since the install sucks.

Hmm, I could put windows on the machine and run from the CD most of the time...

---

### Post by ajgreeny on 2007-09-20
Did you have any add-ons with your mozilla or firefox as they seem to be the things that cause problems as far as I can see?  No problems here with firefox, I must say, and have never really had any either, right through use of the program from version 0.7 or 0.8 on windows up to the 2.0.0.6 at the moment.

Perhaps worth renaming your ~/.mozilla folder as ~/.mozillaold and then copying the various files and folders from that to the new one that will be made when you open the program, one by one.  That may give you a clue what is causing the problem and allow you to fix it.  You can also open the progs with the terminal and see what error messages it throws up, or if any obvious ones tell you the problem.

---

### Post by ender42 on 2007-09-21
>Did you have any add-ons with your mozilla or firefox

I had with firefox.  But I believe I stripped it down, and still hung on me when I tried to save webpages.  I then transitioned to Mozilla, didn't put any addons/plugins for it.  I got similiar weekly-to-daily crashes, but I was able to save webpages - some of the time, the rest of the time Mozilla (and previously Firefox) said it saved, but in reality, itjust saved garbage under the filename.

>You can also open the progs with the terminal and see what 
>error messages it throws up, or if any obvious ones tell 
>you the problem.

Opening via terminal is what I was doing - that was the only way I got 'segmentation fault' for a diagnostic.  

If you just click on mozilla or firefox from the menubar, it just gracefully fails to do a damn thing.  Luckily I know just a tad enough to try launching from console.  But that's all I get, and then the PID disappears, and I get my commandline back.

---

### Post by ender42 on 2007-09-22
Galeon is running pretty damn slow, and crashing every 4-10 hours.  Much like Mozilla and Firefox in the early stages of the game...

---

### Post by undecidable on 2007-09-23
fwiw, and just in case you have not done it,
a (really) clean install always fixes my Firefox problems.

---

### Post by ender42 on 2007-09-24
Oh, believe me I've been thinking about that.  But I thought the whole reason I was using Linux was so that I could diagnose and fix problems, hopefully faster than doing clean installs.  

I mean, if I just need to clean install every month, why not just use windows?  I wanted a working OS.

---

### Post by undecidable on 2007-09-24
I meant a clean install of Firefox, not of Linux.

In any case I am not sure that the difference between Linux and Windows is that on Windows you have to do clean installs and on Linux you do not.   

Also, while there is more information to solve problems on Lx than Wz, it does not mean all problems are solvable in the amount of time you wish to devote to solving it.

---

### Post by ender42 on 2007-09-24
> **undecidable said:**
> I meant a clean install of Firefox, not of Linux.

Okay, in my original message I said:

> But now I've got them segfaulting, and I uninstalled and reinstalled them, usually I was able to get a week or two of use out of each that way, but no luck this time.

I was removing and reinstalling them (is this what you mean by a clean install?): 

apt-get remove mozilla-browser
apt-get install mozilla-browser mozilla-psm
 
Removing mozilla-browser removes mozilla-mailnews and mozilla-psm as well...I skip re-installing mozilla-mailnews, since I don't use mozilla for news.

If that is a clean install, then that 'solution' is not working for me anymore - as I'd said originally.

I used to do a like manuevuer back in the day for firefox, but just gave up on trying to get firefox to work., so I don't have the details on reinstalling firefox.  I did however write a script to kill instances of firefox, since it would hang my machine every day (or 6 hours) or so....  The meat of that script is here:

ps aux|grep firefox|grep -v grep|awk '{print $2}'|xargs kill -9

Any ideas of how to figure out what's crashing/segfaulting/hanging Mozilla (or Firefox), besides the trial and error method ajgreeny has suggested (dick around with every file in my ~/.mozilla folder)?

---

### Post by undecidable on 2007-09-25
I believe "apt-get remove mozilla-browser"
is not sufficiient for a clean install.  
You need to also rename ~/.mozilla folder as ~/.mozilla.old
before then installing
as otherwise many settings get carried over. 
Settings from prev vsns of FFx have been known to cause problems.  

As you are trying to debug
after you install
 add no add-ons (themes or extensions)   - just run it clean.  
I have found this is different from installing add-ons then disabling them later
(which is what you said above you tried). 

If it still fails, on a genuinely clean install (as above)
and with no add-ons
then you have a non-firefox problem.

---

