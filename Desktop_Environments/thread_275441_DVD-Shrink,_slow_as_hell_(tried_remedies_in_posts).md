---
title: "DVD-Shrink, slow as hell (tried remedies in posts) and crashes"
date: 2006-10-11
forum: Desktop Environments
---

### Post by col.cardaki on 2006-10-11
Hi all,

I have recently installed Dapper Drake version of Ubuntu and have wine installed (the most recent version) from the Wine HQ repository and installed DVDshrink and dvddecrypter under wine.  They both "work", in terms of starting up and basically functioning.  I have the most current versions of both.  All patches/updates have been installed as of this writing. I have used Automatix to install the codecs and dvd files, and I also installed k9copy and dvd::rip. 

WINDOWS VERSION:
Dvd Decrypter- NT 4.0 (as mentioned in the threads I looked at)
DVD Shrink- currently NT 4.0, but have tried 2000 and XP... 

The problem is multi-fold.
1) intially, no matter what windows version I set DVD shrink to the shrinking process encodes at under 300kb/s, which takes days to encode a dvd, if at all.  This is the same regardless of whether I encode straight from DVD or if I use dvddecrypter to first rip the .iso to the computer.  

2)  Now however, the computer just shuts down (as if I had hit the "shut down" button) while encoding.  The same happens when I tried to use k9copy.  This has been experienced with a dvd I have been trying to backup (which is not encrypted or anything... it is a yoga dvd).  I have yet to try with other dvd's.  My computer does not "shut itself down" when using dvd decrypter or when it just is running. 

MY QUESTIONS:

1) how can I speed up this process?  My brother-in-law uses Debian (xfce) and his dvdshrink works just like windows did.  His computer has less ram and less processor speed than mine (which is a sony vaio, 512mb ram, 8x dvd-r/w, pentium 4 (2ghz i believe)).

2)  Why is my computer shutting itself down?  I tried to look at the logs but they tell me nothing... there is no error messages, there is no prompt, it just SHUTS down.  Could it be the DVD (although it doesn't crash with dvd-decrypter, so that doesn't make sense).  AS a note, it also CRASHES the same with k9copy, which doesn't seem to work either.  

PLEASE HELP!:eek:  I have mined google, forums, and the wiki, however they are largely out of date.  When they are not out of date, I have tried all the remedies they have suggested and no change.  I have tried "unchecking low priority mode" which did nothing and actually made it work slower apparently.  I have tried everything.  please help!

---

### Post by Aikon- on 2006-10-11
With regards to your second problem, if the "Shutdown PC when complete" option is selected in DVDShrink, try disabling it; perhaps its getting confused somewhere along the way. Failing that, I haven't the foggiest :/

---

### Post by someguyouknow on 2006-10-11
Is it a DVD in particular? 
I know that some DVDs just cant be copied by DVDShrink or k9copy.
those usually lock up my DVD drive.
have you tried more than just one dvd?

---

### Post by col.cardaki on 2006-10-11
I haven't tried anymore dvd's mainly because it takes 2-3 days to encode them, if it all.  

Can anyone whose dvdshrink encodes in a standard amount of time tell me what their wine (and other) settings are and how they set up dvdshrink?  

This way I can emulate that process and maybe I missed something when I installed it.  Figuring on Windows, with deep analysis, it took roughly 2-2.5 hours straight from the DVD, is anyone using dvdshrink and achieves those results?  If so... how did you set yours up?

Thanks for the responses so far.

---

### Post by orb9220 on 2006-10-11
First thing to check is if your cdrom drive has dma enabled. In a term type:

hdparm /dev/hdc  and see if using dma is set to 1

Second did you use winecfg to add the app and set to winXP for dvdshrink?

Using it for me it takes 45-60 mins to rip as iso to hd. Don't know about deep tho don't use it.

---

### Post by col.cardaki on 2006-10-13
Ok, I did a few things, none of which worked.

1)  DMA is turned on (additionally, Dapper Drake ships with it turned on I believe, but either way, it's on now).  No effect on burn speed.

2)  DVDshrink was set to XP and had no affect on the slow burn times, nor the crashing.

3) I removed the repository copy of k9copy and replaced it with the newer package that they have out (1.04 i guess).  That removed the CRASHING problem for k9copy (as it hasn't crashed yet), however that doesn't change dvdshrink's propensity for crashing.  

The bigger problem though is that even though k9copy theoretically works, it has been shrinking this same dvd for 3 days now.  In fact, it has been on "Updating vob..." for 2 days.  It is at 99% done, but this updating process is taking DAYS.  Now this cannot be normal.

orb9220-  what kind of computer are you using?  What version of wine (i have the winehq repository version)?  I don't understand how yours can crank it out in 45 minutes where mine takes 2+ days.  That's abnormal!!!!  

I just cannot find a solution.  I have the same distro as everyone here, the same versions of everything, and followed the same procedures... yet mine doesn't work and everyone else seems to have no trouble.  It's not fair... ["what kind of nihilist are you!]

Thanks for your help so far, hopefully i can get to this bottom of this.

---

### Post by someguyouknow on 2006-10-13
that is odd. it only takes 30-50 minutes for me too using k9copy.
and my comp is pretty weak. 

maybe this guide will help?
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

if you are having a problem with the same dvd, try another one to see if it is the DVD with the problem.

---

### Post by orb9220 on 2006-10-13
Yeah something fishy with your setup > col.cardaki.

Mine is a 1.3ghz-640mb,nvidia fx5200 system. And I used whatever is in synaptic. And I have ripped at least 100 or so dvd movies this way. With rip to iso on hardrive being in the 40-60 min range depending on how much compression it has to do.

---

### Post by col.cardaki on 2006-10-17
I did the same thing you did.  I don't know what to change in my setup.

Oddly enough, k9copy finally finished after 3 days and then told me the volume title was too long and to put in a new disk, which I presumed to mean that it was trying to burn to the actual dvd.  So I put in a new dvd, and then it still says to put in a new disk... so I do, and it continues.  So I hit cancel and then I find no evidence of any .iso file anywhere on my harddrive.  I find the vts files, but I think those were from an experiment with dvd::rip.  

So 3 days of ripping and now I have NOTHING.  It seems to pull the same crap with any dvd I put in... I am at a loss.  I'm gonna keep trying, but if anyone has anything they can think of as possible fix or whatever, please tell me!

---

### Post by col.cardaki on 2006-11-06
So, I have tried many other DVD's and basically the same problem, but not as extreme.  Most DVDs take about 3,4, or even 5 hours to shrink (with DVD Shrink).  That is WITHOUT deep analysis or error correction and with "low priority" mode turned off.  

It generally will start out at like 3,000 kb/s, which is fine... but slowly and inexorably will begin to slow down and slow down until it hits about 400-600 kb/s, if not lower.

Anyone have this problem and fixed it?  I'm not really sure what else to do, my dvd-burner seems to work fine otherwise... I'm at a loss.  I have tried everything over the last few weeks that the posters above have suggested with no change.

---

