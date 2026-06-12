---
title: "Hardy Heron Graphics Slowdown"
date: 2008-04-26
forum: Desktop Environments
---

### Post by the_Ben on 2008-04-26
I just upgraded to 8.04, and I'm experiencing a graphics slowdown.  I currently have the visual effects set to normal (under System --> Appearance), but I also experience a slowdown with visual effects set to "none".  Most notably, a choppy transition when scrolling down a web page.

This was not a problem with 7.10.  Is there some type of graphics driver I'm missing, or am I SOL until some future update?

---

### Post by UniversalMarcos on 2008-04-26
What video card do you have?

In my case I have an nVidia 6100 and when I installed 8.04 it offered to use restricted drivers and using them improves the graphics a lot.

---

### Post by the_Ben on 2008-04-26
I'm not really sure how to check what video card my laptop is equipped with.  As far as the proprietary drivers, ubuntu only offered ones for the software modem and wireless card, both of which work fine.

---

### Post by overdrank on 2008-04-26
> **the_Ben said:**
> I'm not really sure how to check what video card my laptop is equipped with.  As far as the proprietary drivers, ubuntu only offered ones for the software modem and wireless card, both of which work fine.

Hi and you can use the command  ```
lspci 
``` in the terminal. Look for VGA

---

### Post by the_Ben on 2008-04-26
> **overdrank said:**
> Hi and you can use the command  ```
lspci 
``` in the terminal. Look for VGA

Much thanks!  Here's what I get:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
```

So is my best bet to google search for drivers for this?

---

### Post by overdrank on 2008-04-26
> **the_Ben said:**
> Much thanks!  Here's what I get:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
```

So is my best bet to google search for drivers for this?

Hi and one on the beginners team members has some good info
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by the_Ben on 2008-04-26
Tried the solution posted in the thread you linked to, but all it did was switch me to "normal" in visual effects, which I wasn't having any trouble with.

I'm still encountering the same glitchy slowdowns, but I did get an unusual message when I ran this command in the terminal:
```
$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```
I gotta say, I'm tempted to go back to 7.10 and not bother with the new release until I buy a new laptop (as this one is around 4 years old).  :?

---

### Post by fhmanas on 2008-04-26
You are not alone, i don't think it's your video card.  I am experiencing Heron slowdown as well and my video card is not a restricted one (Intel).  If you did the upgrade route, it would be much slower than if you did a fresh install, in any case, 
Heron is slow compared with Gutsy.  Am contemplating on going back to Gutsy.

---

### Post by the_Ben on 2008-04-27
Well, thanks for attempting to help me out everybody, but I think I'm just gonna go back to 7.10 for the time being.  In addition to to the graphics slowdown, I'm also having issues displaying flash properly (which could be a firefox 3 issue), I can't get my printer set up, and some programs like Amarok will show the startup screen but not actually launch.

None of these were issues with good ol' 7.10.  Like I said, maybe I'll wait to get a new lappy and give it another shot later.  Thanks again guys!

---

