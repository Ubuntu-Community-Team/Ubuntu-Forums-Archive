---
title: "[SOLVED] live cd?"
date: 2008-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by allenbradley on 2008-07-16
hey all. I am pretty new to ubuntu, so sorry in advance if the question seems stupid. I recently purchased a dell inspiron 1525 with vista preinstalled ( they do not sell n series in my country ). Now, i want to dual boot ubuntu with vista. I also located a dell ubuntu iso on the website  : 
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)
I have a limited connection, so before i download it, i just want to know whether this would function as a live cd as the only method of installation i know is via live cd. So any help would be really appreciated, so thank you in advance!

---

### Post by unutbu on 2008-07-16
These threads: [http://ubuntuforums.org/showthread.php?t=793179](http://ubuntuforums.org/showthread.php?t=793179)
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525)
may be of interest to you. Primski reports on May 14, 2008 that a generic Hardy installation works well. ndiswrapper may be required to get wireless working.

The link you mentioned shows that there are a number of known issues using the custom image with the 1525, and links which describe fixes. You might want to carefully compare the Known Issues and their fixes from the dell wiki, against what's reported to work out-of-the-box in Hardy on [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525).
As an example, Dell provides a fix to get Compiz working with their custom Gutsy image, but compiz works out-of-the-box with Hardy according to the wiki.ubuntu.com page.

Hardy has LTS (long-term support) which is also an attraction.

---

### Post by allenbradley on 2008-07-16
hey thanks for the quick reply. So i guess i'll go along with a generic install like primski. One final question though.. are drivers available for the 64 - bit version of ubuntu 8.04?

---

### Post by unutbu on 2008-07-16
There is a forum sticky on this topic: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)
My knowledge is very limited in this area, so it's probably best to get your information from there.

From what I've read, 64-bit users may face a few extra hurdles getting things to work. If you don't mind seeking some fixes for problems on the forums, then I think most users can get 64-bit machines working with a bit of persistence. However, if you want the most components/apps working with the least amount of hassle, I think 32-bit is still a bit easier. 

If the sticky doesn't answer your question, then perhaps post a message in the 
x86 64-bit (Users [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)) forum.

---

### Post by allenbradley on 2008-07-16
hey thanks a lot. I guess i'll go with 32 bit as 64 seems to offer no big advantage for me. But thanks again for the amazingly quick responses.

---

### Post by LeoSolaris on 2008-07-17
You probably will not catch this, but I have a 1520, just a little back from yours, and it works just ducky with 64 bit. There are some small things to tweak for 100% use, but none of them are hard.

Leo

---

### Post by modena on 2008-07-17
If you feel that your touchpad is too hot, get the 64 bit.
I have an inspiron 1525. 
The only thing I don't like about it is the heat on the touchpad / glidepad / whatever they call those things this week.
I originally installed 32 bit ubuntu 8.04 and found that the touchpad got even hotter with linux that with xp or vista.
On my particular laptop that was really uncomfortable.
I was just about to give up on linux on the 1525 :-( when somebody on this forum said that they had the same heat issue but that the *64 bit* ubuntu only heats the computer up the same as xp.
Worked for me.

I had no noticable problems with 64 bit compared to 32 bit.  More to the point, any issues I experienced on 64 bit also exist on 32 bit.  JDK6 has a few annoying bugs and flash has a few annoying bugs on both 32/64 bit.  

I had no problem with wireless (4965agn) or any other hardware.

---

### Post by allenbradley on 2008-07-18
thanks for the suggestions guys! just one q however.. i read in another thread about how 64 bit flash for ubuntu is not available yet... so do you guys watch youtube/metacafe by downloading them and watching with ffplay?

---

### Post by jost1989 on 2008-07-18
I'm thinking of dual booting my 1525 with Ubuntu, why does the touchpad thingy get hotter? I've never really noticed any heat problems with it running Vista.

---

### Post by modena on 2008-07-19
allenbradley, I have the adobe version of flash player. I don't know how to tell if it is 32 or 64 bit - I just got it from synaptic. I am able to able to watch youtube movies in firefox, but I don't watch much of that stuff so it's possible that you may find issues that I haven't. I don't think the free versions of flash player (gnash/swfdec) work as well with youtube / firefox.

jost1989, I'm not sure it is *actually* the touchpad that has the heat problem. On my particular laptop the bottom-front-centre (just under the touchpad) gets really hot. This in turn heats the touchpad. 
I run ubuntu most of the time and xp sometimes. It *seems* to me that the laptop fans run much more frequently under xp which probably explains the difference.  Note: I tried i8K on both ubuntu and xp and it shows the temps but doesn't actually control the fans on a 1525.
Sorry but I don't have enough (any) knowledge of the kernel internals which could explain why linux would make computer parts run hotter. Different drivers / process scheduling / memory usage, who knows? If you search on the web you'll find posts about linux systems running hotter than windows (sometimes overheating), but I never found and answers as to why. 
So I hope you are lucky and don't have temperature issues, but if you do 64 bit may be a help. I'm sure there's a reason why people generally recommend 32 bit, but in my normal use I've had no probs or limitations with 64 bit.

---

### Post by ocap on 2008-07-26
I proved the 64bits version of kubuntu hardy live-iso with my inspiron 1525, but the trackpad temperature is more or less the same than with the 32bits version that i have in the hd. Would it be different if i install on the hd the 64bits version?
I have BIOS A13. Don't know if it is relevant.
Thank you.

---

### Post by modena on 2008-07-31
ocap, 

Do you mean that running 32 bit your touchpad gets *really hot* or just *kinda-warmish*?  

I think you should only look at changing if it gets really hot - like as hot as the hottest part of any laptop you have ever felt.  

It seems that the 1525 will always be at least warm on the touchpad because the designers put something under there that either works too hard (especially running linux) or doesn't get enough ventilation.

I guess it's possible that running the 64 bit live cd also makes everything feel hotter than it would installed to the hd because the dvd drive works so hard during a live cd boot.  So it's up to you decide if it's worthwhile installing the 64 bit to the hd.

---

