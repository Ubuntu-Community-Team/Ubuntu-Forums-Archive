---
title: "Desktop Wall Viewport Switching Preview - Corruption?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Draton on 2007-10-23
Hi, I searched around the forums and was unable to find anyone with a solution to this problem.  For some reason when I activate the Desktop Wall plugin in Compiz, and use the "Viewport Switch Preview," the actual preview looks as though there is graphical corruption.  The gradient is not properly displaying and the arrow looks pixelated.  Has anyone had a similar problem with this?

It should probably be noted, my system is configured as follows:
Intel Q6600 @ 3.0ghz
GeForce 8800 320mb
4gb of ram
32-bit Ubuntu 7.10

Any help is greatly appreciated.
Thanks,
-Kevin

---

### Post by Draton on 2007-10-23
I am still having this problem, it seems that I get close to "no corruption" when I change the virtual desktop size, but it still displays a horrible gradient and strange pixels around the arrow... has anyone else had this problem?  I could probably take a picture w/ my digital cam but not sure if a prntscrn will work on it.

---

### Post by ZeusABJ on 2007-11-27
I too am having this problem. No solution to report as of yet.

---

### Post by ZeusABJ on 2007-12-02
Does no one have an answer for this issue? Surely we can't be the only ones...

---

### Post by ZeusABJ on 2007-12-10
Don't kill me but I have to do this...

*bump*

I just have to know whats going on here. I know its a minor bug but its the not understanding why its happening that is driving me nuts. Surely someone out there knows the cause of this issue...

---

### Post by imacoorobot on 2007-12-23
Here's a screen.

Nvidia Quadro NVS 140M myself.

---

### Post by ZeusABJ on 2008-01-05
> **imacoorobot said:**
> Here's a screen.

Nvidia Quadro NVS 140M myself.

That is *EXACTLY* whats happening to me! Still no response form anyone though. I'm thinking this has to be driver related. Looks like we are all nVidia users, so that looks to be our commonality. The good news is I read that nVidia recently released a new stable Linux driver with better support for later cards, however it does not appear to be included in any of the repositories (Multi or Uni). Before Gutsy I always used Alberto Milone's great Envy utility ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) to install the latest nVidia drivers. I checked and he has update dit to include the latest stable nVidia driver. I guess I'll give that a try and report back if it fixes my issues.

---

### Post by ZeusABJ on 2008-01-06
YAY! I'm happy to report that using Envy to install the new stable nVidia driver WORKED! Since installing the new driver I've noticed an improvement in overall system performance and *ALL* my graphics corruption issues seem to have been eliminated. The best part is (since this is a stable release) its sure to be included in Hardy Heron which means (in April) those of us with 8000 series nVidia cards should no longer have to deal with this issue. Again here's the link to Alberto's site (if anyone wants to try my solution):

[http://albertomilone.com/](http://albertomilone.com/)

Amazed I was able to fix this out on my own (given my somewhat limited knowledge) this. You'd think someone far smarter than I would have been kind enough to at least respond and say "its a driver issue". Oh well, I guess this is a busy board.

---

### Post by frotzed on 2008-04-17
I was having the same issues with my new Dell and using Envy to install the nVidia drivers fixed the problem for me as well.  Great sleuthing!

My system is as follows:
Dell Inspiron 530
4GB RAM
2.33 Intel Core2 Duo E6550 (4MB L2 Cache,2.33GHz,1333 FSB)
nVidia GeForce 8600GT-DDR3 256MB

---

