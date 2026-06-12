---
title: "Dual monitor sticky edges adjustment"
date: 2012-04-29
forum: Desktop Environments
---

### Post by dhysk on 2012-04-29
Is there a setting or a value in some config file I can set the 'stickiness' of the sticky edges?

I have 2 monitors and I like having the sticky edges so I can use edge detection on the screens to get 1/4 and 1/2 size windows easy.

I also like it so I can use the dock on both screens that way I can control what screen the new program will open on.  In 11.10 it would choose a screen at random it seamed.

The issue is that I have to move the mouse to fast for it to not stick and what I would call hold is a bit to tight.  If I'm just naturally moving the mouse from one screen to the other it gets stuck in the middle, and than it takes me a second to get it out of there.

If there is a setting I'm sure I could adjust it to better suit me.  If there isn't a setting who do we contact to get a setting put in place for the next Ubuntu 12.10?

---

### Post by *M* on 2012-04-29
Have a look at CompizConfig Settings Manager (might need to install from software center), under Ubuntu Unity Plugin > Experimental there's an option called edge stop velocity, I think that may be what your looking for or one of the options above it.

---

### Post by dhysk on 2012-04-30
PERFECT!!... 

Saved me so much time.  I've had that thing installed since about 8.04 ;).

Right now I have them set at

Launcher Reveal Pressure = 3
Launcher Edge Stop Overcome Pressure = 15
Pressure Decay Rate = 3
Edge Stop Velocity = 10

Feels much smoother and usable now.  I have to pause to get the launcher to pop out and to drop the windows on the edges now.  Which is much better than having to pause to get from one screen to the other.

---

### Post by witakr on 2012-09-05
> ***M* said:**
> Have a look at CompizConfig Settings Manager (might need to install from software center), under Ubuntu Unity Plugin > Experimental there's an option called edge stop velocity, I think that may be what your looking for or one of the options above it.


I was having this same problem and this fixed it. Thank you!

+1 for googling first...lol

---

### Post by studiogrynn on 2012-12-13
> **dhysk said:**
> PERFECT!!... 

Saved me so much time.  I've had that thing installed since about 8.04 ;).

Right now I have them set at

Launcher Reveal Pressure = 3
Launcher Edge Stop Overcome Pressure = 15
Pressure Decay Rate = 3
Edge Stop Velocity = 10

Feels much smoother and usable now.  I have to pause to get the launcher to pop out and to drop the windows on the edges now.  Which is much better than having to pause to get from one screen to the other.
Tried your settings. Work great! Thank you all for your contributions.

---

### Post by igodspeed on 2012-12-28
> ***M* said:**
> Have a look at CompizConfig Settings Manager (might need to install from software center), under Ubuntu Unity Plugin > Experimental there's an option called edge stop velocity, I think that may be what your looking for or one of the options above it.


Hi,

I installed it but for some reason I do not have the experimental plug-in in Unity.  Is it something that can be installed? I have attached a screenshot of the screen. Please advise. 

Warm Regards

---

### Post by Jetro on 2013-02-25
igodspeed, the Ubuntu Unity Plugin category should be under **Desktop**.

I also do thank for the topic and answers, made the sticky edge less sticky. ;)

---

