---
title: "What is normal refresh rate for external 19&quot; LCD Monitor?"
date: 2009-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-07-21
Hi,
i have dell mini 9 with Ubuntu 9.04 and external 19" Acer Monitor. Resolution is set on 1366x768, and refresh rate on 60 Hz. I have no other refresh rate option.
Is it normal rate or it should be higher? I notice every on-two minutes this blining (refreshing probably). Is that normal (because i didn´t notice it with Dell´s Ubuntu Hardy)? Is it possible to set higher refreshing rate?

Thanks

P.S. Maybe the refresh rate is not the problem-i have no headache or any other problems-just this blinking every once a while-want to know what is the source...

---

### Post by prshah on 2009-07-21
> **vickoxy said:**
> refresh rate on 60 Hz.

Most LCD monitors have a fixed refresh rate of 60Hz. Check your power cord; it may be loose and causing this problem.

---

### Post by Grenage on 2009-07-21
Most LCDs have a default refresh rate of 60Mhz, but allow you to go higher.  To be honest you'd have a hard time noticing the rate of refresh above 60Mhz on an LCD, but some people are more 'fragile' than others.  A CRT with less than 85Mhz would give me headaches and nosebleeds within 3 minutes, it was actually painful looking at it.  That said, 60Mhz on LCD is fine for me.

I'd check for external sources of interference first, the LCD is unlikely.

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> Most LCDs have a default refresh rate of 60Mhz, but allow you to go higher.  To be honest you'd have a hard time noticing the rate of refresh above 60Mhz on an LCD, but some people are more 'fragile' than others.  A CRT with less than 85Mhz would give me headaches and nosebleeds within 3 minutes, it was actually painful looking at it.  That said, 60Mhz on LCD is fine for me.

I'd check for external sources of interference first, the LCD is unlikely.

Well, i noticed this as i installed jaunty few days ago. Before that i had dell´s ubuntu, but noticed no such things. All circumstances are all the time unchanged.

---

### Post by kostkon on 2009-07-21
Yes, maybe interference coming from the graphics card...

---

### Post by Grenage on 2009-07-21
> Well, i noticed this as i installed jaunty few days ago. Before that i had dell´s ubuntu, but noticed no such things. All circumstances are all the time unchanged.

Ok, so we can rule out external interference.  What graphics card does the computer have, and what drivers are you running?

---

### Post by Shpongle on 2009-07-21
> **kostkon said:**
> Yes, maybe interference coming from the graphics card...

yea id say thats most likely it, dell usually require certain drivers for display , i was fixing a dell pc yesterday and it would not let me set the resolution until i got the dell driver, mabye the upgrade changed some settings, did you check their website ?, or connect it up and try system->admin->hardware drivers? or can you go into the moniter settings by buttons on the monitor?, or if you have a manual with it , it might provide some insight,

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> Ok, so we can rule out external interference.  What graphics card does the computer have, and what drivers are you running?

Well, i have standard dell mini 9 with  Intel GMA950... I have no other drivers installed-just made Ubuntu 9.04 Installation and nothing else.

---

### Post by vickoxy on 2009-07-21
> **DillByrne said:**
> yea id say thats most likely it, dell usually require certain drivers for display , i was fixing a dell pc yesterday and it would not let me set the resolution until i got the dell driver, mabye the upgrade changed some settings, did you check their website ?, or connect it up and try system->admin->hardware drivers? or can you go into the moniter settings by buttons on the monitor?, or if you have a manual with it , it might provide some insight,

I did manually setup. When i open Hardware drivers-there is only for Broadcom STA-Funk Lan. I didn´t go to their web site (i thought that they have only lpia hardy drivers).

---

### Post by Grenage on 2009-07-21
Well iirc the GMA950 driver is included by default in Ubuntu.  If you:

sudo dpkg-reconfigure xserver-xorg

You can attempt to reconfigure things and see if that helps?

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> Well iirc the GMA950 driver is included by default in Ubuntu.  If you:

sudo dpkg-reconfigure xserver-xorg

You can attempt to reconfigure things and see if that helps?

I did it. This is output. But nothing changed...

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090721134609

---

### Post by Grenage on 2009-07-21
I don't know if there is a proprietary driver that might be worth a shot; hell, it might be what dell use.  I'm off out for a few hours but if you've not had any luck then I'll dig around.

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> I don't know if there is a proprietary driver that might be worth a shot; hell, it might be what dell use.  I'm off out for a few hours but if you've not had any luck then I'll dig around.

Well. i am not sure if i am ready for experimentig with some extra drivers. As said, it comes every 1,5-2 min. I googled it a little, and i found that maybe CPU is causing that (dell mini 9), but strange that something like that wasn´t noticable with dell´s Ubuntu. 

Just to be sure-internal dell´s monitor is working just well.

---

### Post by vickoxy on 2009-07-21
There is some difference though- i use in Jaunty Compiz extra visual effect, which i did not have in dell´s Ubuntu....

---

### Post by Grenage on 2009-07-21
Well fair enough if you don't wish to dabble with drivers and the like; you can always try other things.  If you disable compiz do you still have the problem?  If you run a live CD, does the problem still occur? etc.

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> Well fair enough if you don't wish to dabble with drivers and the like; you can always try other things.  If you disable compiz do you still have the problem?  If you run a live CD, does the problem still occur? etc.

Ok, it seems that "extra visual effects" are cause of these glitches. I just selected "normal visual effects" and so far- nothing. I think i can live with these glitches-they come randomly-sometimes after 5-6 min-and it is just a matter of one milisec.

Thanks for suggestions-at least we found the cause...

I suppose there is no easy adjust/fix for these extra visual effects?

---

### Post by Grenage on 2009-07-21
Unfortunately I have never encountered this problem before, and don't have a system with that GFX chipset to play about with.  It really could be 'anything', but I suppose I'd still be looking at drivers as an important avenue of exploration.

---

### Post by vickoxy on 2009-07-21
> **Grenage said:**
> Unfortunately I have never encountered this problem before, and don't have a system with that GFX chipset to play about with.  It really could be 'anything', but I suppose I'd still be looking at drivers as an important avenue of exploration.

Well, compiz is activated by default in Ubuntu 9.04-so, the compiz is running also when i choose Normal Effects/None. So it is not the compiz itself the problem-only the part "extra visual effects".
Maybe some drivers would remove this problem, and that option would be for me if i:
1) can install it from Synaptic
2) can install it whitout crushing my system (i am newbie, i succeeded it once with mail notifiers, but that is different story...:D)

? Any suggestion?

---

### Post by Grenage on 2009-07-22
I'll have a looksee around and see if I can find something, it's a common gfx card, and ubuntu is a common OS, so there is a good chance it will be a simple process.

---

