---
title: "Compiz broke, drop shadows are now black borders, visual effects cause system lag"
date: 2009-11-14
forum: Desktop Environments
---

### Post by polarberg on 2009-11-14
Everything was working beautifully until a moment ago. I don't know which one of these things caused the problem but I'm sure it's one of them:
- I installed and updated a bunch of packages. None of them had to do with Compiz as far as I know. I don't know if Synaptic logs install times by default. The updates went swimmingly and I ran the system for some time on the same boot with no problems.
- I tried to install FL Studio in WINE. Oops. Got several warnings during the install process but it completed. Running it for the first time caused everything to freeze up (FL has this nasty habit of wanting all your screen real estate as well), chunking along giving me errors and generally being a grump. The Force Quit frontend wasn't working and I couldn't find the process to kill it in Terminal so I restarted.

Here's where the fun begins. When I log back in everything is still working just fine, except there are black borders around all my windows, panels and tooltips. Dragging windows is slow and chunky and the system just seems to be slow. Searching around tells me that it's a problem with Compiz's dropshadows. I *had* Visual Effects set on Fantastic or whatever (jello windows and the like) cos it's pretty and I'm not doing any intenseness on this system yet. Only turning them off completely makes the problem go away, as may be obvious.

Since I have no idea - well, two vague ones - what might've caused the problem out of the blue, I don't really wanna go poking around in Compiz's configuration files. I'm on a Lenovo ThinkPad with an ATI chipset and I literally reinstalled Ubuntu (64-bit Karmic) this morning, fresher than a suffocating fish.

It'd be awesome to get a definitive answer on how to reconfigure Compiz to fix this. Every thread I've seen is vague, misleading or abandoned.

P.S.: FL was having trouble rendering its windows and letting me move them, but I'm not experiencing any of the same problems and I don't think Compiz handles them. In other words, this clue is very hard and I think it's pointing in the wrong direction.

---

### Post by jeb800e on 2009-11-14
[http://ubuntuforums.org/showthread.php?t=1326479](http://ubuntuforums.org/showthread.php?t=1326479)

---

### Post by polarberg on 2009-11-15
Awesome. Now my graphics *don't work at all.* Thanks.

No update was required. Karmic doesn't ship with an older kernel. I'm not reverting or giving up and leaving the visual effects off, especially considering that it *was* working this morning and simply *stopped* working this afternoon.

So the option that leaves, among the limited you presented me with, was looking for the proprietary driver. Went into the Hardware Drivers frontend and saw an "ATI/AMD" driver of some sort which wasn't activated it. Downloaded, installed, rebooted: terminal. And now that my X is gone entirely (startx: error: no screens found), I have no idea how to revert the change that I made.

So while I'm waiting for someone to help me, rather than pointing me to another vague, misleading, abandoned thread (this is my sour face), would anyone mind explaining how I fix this new mess?

Again, the aim was to find a solution to this very specific set of Compiz screwups, or at the very least identify what is going on, since this is not an isolated issue. Not to muck through generic graphics fiddles until something works.

---

### Post by luxOFlux on 2010-01-17
Same problem here. Fresh 0910 install worked for a few days then broke spontaneously.

---

### Post by rulesmaster on 2010-04-17
Same problem here.

I think is serious when, out of nowhere, things like this happens. 

What I've done:

1.- Rebooted to all my installed kernels. I have a RT kernel besides the normal updates. So I had three choices. the -20 the -14 and the -9rt.

No Go


2.-Deleted all the settings files in my user. I.e. .compiz /.config/.compiz /.gconf/apps/compiz and everything I could find in my home folder related to compiz.

No Go

3.- Created a fresh new user. Same issue there

No Go.

4.- Completely removed compiz and all the libraries related, rebooted and reinstalled.

No Go.


I really think that this is a serious bug of sorts.

Karmic Koala on an ATI X200 that was working yesterday night. I shut down. Power on today, same issue of the initial post.

No Go.

---

