---
title: "Major ubuntu problems help asap!"
date: 2009-05-02
forum: General Help
---

### Post by The-ITu on 2009-05-02
hi all

i am have major ubuntu problrms.
im runing ubuntu 9.04 (jaunty jackslope) 

when i start up my laptop with the charger in is dose this file check thing and then  it gives my lots of trouble and i just restarts my computer without the charger.

then in the first phew seconds every thing is fine but then is i haven aledy opend up firefox it won let me. everything seems to be screwing up.

look at what the terminal looks like.
o wait i cant show coz the prtsc button isent doing anything.
well any way nothing is realy working.
i cant open any files. the have a loked icon thing abov them.
i cant open any progames. 

when i try and restart the x server is gives me a NASTY error messag that looks just like the blue screen of death. 
it told me to check the syslog BUT I CANT!!!!

Edit: also when i close the lid the it just shows a black screen and the mouse is there but thats about it.

some one help please!!

---

### Post by Alterax on 2009-05-02
Let it finish the filesystem check.  If it didn't need it, it wouldn't ask.  Circumventing safety measures like that is an easy way to guarantee future problems.

> **The-ITu said:**
> hi all

i am have major ubuntu problrms.
im runing ubuntu 9.04 (jaunty jackslope) 

when i start up my laptop with the charger in is dose this file check thing and then  it gives my lots of trouble and i just restarts my computer without the charger.

then in the first phew seconds every thing is fine but then is i haven aledy opend up firefox it won let me. everything seems to be screwing up.

look at what the terminal looks like.
o wait i cant show coz the prtsc button isent doing anything.
well any way nothing is realy working.
i cant open any files. the have a loked icon thing abov them.
i cant open any progames. 

when i try and restart the x server is gives me a NASTY error messag that looks just like the blue screen of death. 
it told me to check the syslog BUT I CANT!!!!

some one help please!!

---

### Post by The-ITu on 2009-05-02
> **Alterax said:**
> Let it finish the filesystem check. If it didn't need it, it wouldn't ask. Circumventing safety measures like that is an easy way to guarantee future problems.

Its not me that dosent let it!!!!
I want it to but it dosent!!

---

### Post by BslBryan on 2009-05-02
I don't really understand your problems, necessarily, but if it isn't working with anything, I'd suggest downgrading to a different version of Ubuntu, or just scrubbing it altogether.  

Why didn't you try it before installing it?  That's the beauty of the LiveCD.  This lets you test compatibility with your machine.  What are the specs of your machine, by the by?

---

### Post by The-ITu on 2009-05-02
> **BslBryan said:**
> I don't really understand your problems, necessarily, but if it isn't working with anything, I'd suggest downgrading to a different version of Ubuntu, or just scrubbing it altogether.  

Why didn't you try it before installing it?  That's the beauty of the LiveCD.  This lets you test compatibility with your machine.  What are the specs of your machine, by the by?

i was runing Ubntu 8.10 for about 7 weeks and then Ubntu 9.04 ever since it came out but only recenlty its been doing this (today and a bit of yestarday.).

p.s i never tryd the beta becuse i cant stand beata versions of things.

---

### Post by ed-koala on 2009-05-02
Boot from the LiveCD and run the file check.  Perhaps a sector went bad and messed up your install?

---

### Post by The-ITu on 2009-05-02
> **ed-koala said:**
> Boot from the LiveCD and run the file check.  Perhaps a sector went bad and messed up your install?
like i said earlier:
im no stranger to ubuntu. if there was something wrong with my install it would have shown up ages ago.

---

### Post by BslBryan on 2009-05-02
Boot into recovery mode with your LiveCD, is all I can think of.  You can also try ```
sudo apt-get install -f
``` to fix broken packages.

---

### Post by HavocXphere on 2009-05-02
nevermind

---

### Post by The-ITu on 2009-05-02
> **BslBryan said:**
> Boot into recovery mode with your LiveCD, is all I can think of.  You can also try ```
sudo apt-get install -f
``` to fix broken packages.
1. i tryd that already
2. i tryd fixing broken packages with recovery mode, but otherwise my terminal is fully screwd up!

---

### Post by BslBryan on 2009-05-02
> **HavocXphere said:**
> nevermind

All right, then. :confused:

---

### Post by HavocXphere on 2009-05-02
It would help if you elaborated on the "lots of trouble" part. Did it give you an error message perhaps?:confused:
> when i start up my laptop with the charger in is dose this file check thing **and then it gives my lots of trouble and** i just restarts my computer without the charger.

It would also help to know what filesystem we are talking about...

Ext4 for example does not like frequent restarts:
[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199)

> All right, then.
I posted something and instantly regretted it...and couldn't find the post delete button.

---

### Post by Carl Hamlin on 2009-05-02
Sounds like a class III toast, to me. If it were me, I'd call it, backup data, smoke the drive and reinstall.

And if that didn't work, I'd start thinking about acquiring a new drive.

---

### Post by The-ITu on 2009-05-03
this problem seems to have fixed itself.
il keep you updated just in case :)

---

### Post by The-ITu on 2009-05-04
seems to have fixed its self.
thanks anyway guys :):):P

---

### Post by The-ITu on 2009-07-22
sorry for triple posting but this problem has returned. and this time im not *as* much of a noob as before so I can help you help me better.
I think it has something to do Jaunty. any way, in answer to HavocXphere question, yes my file system is ext4, but like you suggested I waited a long time before restaring. 
the thing about the file system check is now gone, I relised I just had to wait a bit.
the problem has got worse now. it wont even let me log on any more. after i type in my user name a pass word the log on screen gos away and nothing hapends.

I have a question tho, is there a way i could use my ubuntu 8.10 (it does not use ext4) CD to *down*grade back to 8.10 without harming my files?
a detales tutorial would be apreitiated.

apolagies for bad spelling,
I will bump if needed,
thanks to all who have and will help me.
  ________
_|-The-ITu-|_

---

