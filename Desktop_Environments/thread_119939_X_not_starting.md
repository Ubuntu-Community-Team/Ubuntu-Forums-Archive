---
title: "X not starting"
date: 2006-01-20
forum: Desktop Environments
---

### Post by s1gnAl on 2006-01-20
I believe X is having trouble starting up on my laptop, I am running a Sony VAIO laptop and this is a new install. It was running fine right after the install, but when I rebooted the machine appeared to go through init and then I was presented with a blank black screen and no disk activity. I let it sit for a few moments, but I ended up having to power the machine off. I also did a reinstallation to see if that would clear my problem, but no such luck.

My laptop specs are as follows:
Sony VAIO PCG-K45
3.2 Ghz Pentium IV
1 gigabyte PC-3200
80 gig hard drive
ATI RADEON IGP345M video chipset 128mb (shared)

I am also dual booting with Windows XP and I have not had any issues using that, so I don't believe this is a hardware problem. 

The only thing I can think to do is boot a knoppix CD and mount my partition and look at the logs, are there any utilities, etc on the Ubuntu CD that would help me more efficiently?

---

### Post by christhemonkey on 2006-01-20
After it has run through the init proccess, can you get into a terminal?
(type Ctrl+Alt+F1)

---

### Post by s1gnAl on 2006-01-20
[QUOTE=christhemonkey]After it has run through the init proccess, can you get into a terminal?
(type Ctrl+Alt+F1)[/QUOTE]

Ahh didn't think of that, I don't have it in front of me at the moment(Im at work), but I'll try that when I get home. Anything else I should try?

---

### Post by christhemonkey on 2006-01-20
if you can get into a terminal, then try:
sudo dpkg-reconfigure xserver-xorg 

Then select anything appropriate!

---

### Post by s1gnAl on 2006-01-20
Still not getting anywhere with this. I was able to boot off of a Knoppix CD, mount my linux partition and I poked around in the logs, but that did not yield many results(if I looked at the right ones anyhow)

Also looked around at xorg.conf, and everything appears to be correct there as well. The baffling thing is that I was able to install and it worked fine, but when I rebooted it for the first time, this is when it happened.....

---

### Post by crispy_420 on 2006-01-20
What driver are you using? I heard that sometimes onboard video from ATI needs to be setup us as vesa and then later configured. Maybe be wrong though but what do you have to lose at this point.

---

