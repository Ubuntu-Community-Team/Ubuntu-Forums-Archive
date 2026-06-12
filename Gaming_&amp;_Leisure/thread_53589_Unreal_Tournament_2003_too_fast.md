---
title: "Unreal Tournament 2003 too fast"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by St3althcAt on 2005-08-01
Hello guys!
I've installed Unreal Tournament 2003. The problem is that, when I play the game, it runs too fast! I've followed another post here, it had a solution for UT, tried to adapt it to UT2003 but without success. Can someone tell me how to solve this, please. It's very hard to shoot a bot when is running like 200 Km/h :P!

Thank you.

---

### Post by somuchfortheafter on 2005-08-01
look at the bright side. with your increased speed. in a lan game you will be faster than anyone else and will strike with deadly precision thus eliminating the other chumps who think they can frag.. \\:D/

---

### Post by kaffeend on 2005-08-01
Just a thought here - if UT 2003 is a 32 bit software, are you using Ubuntu for AMD 64? Thus doubling your processing speed of a 32 bit game? If so, this is very interesting indeed! :)

---

### Post by rvarma on 2005-08-01
Are you using a pc with CPU scaling? If you are, disabling that will most likely fix it; it did for me.

---

### Post by ritual on 2005-11-29
I'm having this same problem. First of all, I have to set my screen resolution to 800x600 before even starting the game, or else I will just have sound with no video, but when I do get the game running, it is way too fast paced.

I'm running the 32 bit version of Ubuntu but I do have an AMD64 3200+ processor. I've looked around the net and haven't found a fix. Any suggestions?

---

### Post by Chal on 2005-12-15
try

sudo killall powernowd

before starting the game 

hope it works for you 

CHAL

---

### Post by Pescar on 2007-07-23
WOOOO!!!! I got it! after trying for days with it sometimes running fine and (mostly) WAY too fast, i found something from a windows guide.  I have an athlon64 3200 btw, running 32 bit ubuntu and i didnt have any powernowd process running.


go to /home/me/.ut2003/System and open UT2003.ini . 
Under [Engine.LevelInfo] add the following line: bCapFramerate=True
that's it! caps your framerrate at 90 i think. 
not that anyone cares for ut2003 any more.

---

### Post by mikeym on 2007-09-17
I do!

---

### Post by mikeym on 2007-09-18
Can I just say the most random thing has happened. When I first tried the bCapFramerate=True suggestion it worked like a charm but then I restarted the game and it stoped working!

Now if I set bCapFramerate=False it works! 

It's like it's setting the opposite of what I tell it to.

---

