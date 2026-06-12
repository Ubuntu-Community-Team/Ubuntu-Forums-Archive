---
title: "Issues when gaming in general"
date: 2009-02-01
forum: Gaming &amp; Leisure
---

### Post by Rumbl3 on 2009-02-01
When i pay anything Urban terror or say quake wars linux demo. After a little bit i get a black screen and the game screen is then put into window mode and its frozen. The game is still running and everything. But I can't control or do anything i end up having to just restart my machine. 

Btw i'm new to linux is there anything like windows has for ctrl+alt+del to bring up the process manager and end somethign that is frozen? Just wondering if linux has something like that.

Also could this be the screen saver coming on? or maybe my monitor going into sleep mode?

---

### Post by RaiCoss on 2009-02-01
> **Rumbl3 said:**
> When i pay anything Urban terror or say quake wars linux demo. After a little bit i get a black screen and the game screen is then put into window mode and its frozen. The game is still running and everything. But I can't control or do anything i end up having to just restart my machine. 

Btw i'm new to linux is there anything like windows has for ctrl+alt+del to bring up the process manager and end somethign that is frozen? Just wondering if linux has something like that.

Also could this be the screen saver coming on? or maybe my monitor going into sleep mode?

Okay, a couple of things, when posting a fault, it's usually best to detail your PC specs, and what version of Ubuntu your using  (8.10 Intrepid ~ 8.04/8.04.1 Hardy) etc...

As for your problem with the little knowledge i can gather from your description, it could either be because you have Compiz enabled(the wobbly windows thing), you have dodgy graphics drivers (ATi drivers are seriously dodgy), running 3D app's overheats your graphics card, or you have a more serious issue with Ubuntu itself.

---

### Post by Rumbl3 on 2009-02-01
lol sry
athlon 64 x2 (939 socket) 3800+ oc'ed to 2.7 ghz
4 gigs of ocz ddr 400
DFI lan party SLI nf4 mobo
Geforce 9600GT 512mb
two 100 gig hd's
Ubuntu 8.10

No it's not overheating either. Not even close. 

I think its teh screen saver. I changed its time to come on after 25 minutes and wouldn't you know it the problem (wasn't keeping track of time exactly) happened about 25 to 30 minutes into gaming.

Some reason it must not know that the computer is being used. Least that's my 2cents lol.

---

### Post by RaiCoss on 2009-02-01
> **Rumbl3 said:**
> lol sry
athlon 64 x2 (939 socket) 3800+ oc'ed to 2.7 ghz
4 gigs of ocz ddr 400
DFI lan party SLI nf4 mobo
Geforce 9600GT 512mb
two 100 gig hd's
Ubuntu 8.10

No it's not overheating either. Not even close. 

I think its teh screen saver. I changed its time to come on after 25 minutes and wouldn't you know it the problem (wasn't keeping track of time exactly) happened about 25 to 30 minutes into gaming.

Some reason it must not know that the computer is being used. Least that's my 2cents lol.

Hmmmmm, if i was you I would disable the screensaver, and stop the overclock on your CPU. If that dosen't do anything then it way well be a dodged up install of Ubuntu, as your system should be 100% perfect xD

[[EDIT]] Are you using 32 or 64 bit??

---

### Post by Crafty Kisses on 2009-02-01
What are the results of this command?
```
glxinfo
```

---

### Post by eragon100 on 2009-02-01
Just disable compiz if it's enabled, that should simple fix the problem.

Go to System -> preferences -> appearance and then to "Visual effects" and select none. That will fix the problem with your games chrashing to a window. Nothing more will be required.

If it still doesn't work, post the output of the command posted above, please :wink:

---

