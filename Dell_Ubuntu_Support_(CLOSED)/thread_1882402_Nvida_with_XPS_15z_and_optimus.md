---
title: "Nvida with XPS 15z and optimus?"
date: 2011-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Biciclettapc on 2011-11-17
Help!

May have purchased this laptop with false hopes.....based on some threads I'm reading.  I guess I should have read before I purchased but still time to send back to Dell if its a issue.  

Can and will the Nvidia card work under 11.10?

I do NOT want the intel graphics and want the Nvida card to work.  I run Compiz under unity on my other systems and want the same here.

Paul

---

### Post by Trilby on 2011-11-17
Just bought a XPS 17 with a dedicated Nvidia graphics card using optimus. Apparently, on Linux, both it and the integrated card will draw power, but only the latter will do anything. :-(

EDIT: Maybe look at: [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by Trilby on 2011-11-28
I've tried a wubi install on the aforementioned laptop. There appear to be drivers for the graphics card, although as far as I can tell, the dedicated graphics run continuously. The laptop gets a bit warm but battery life doesn't seem to badly affected.

I'll keep you posted. Information to follow when I work out exactly what's going on.
[B]
UPDATE 1:[/B] Don't install the Nvidia drivers on restricted extras, at least not for now. This will make the dedicated graphic draw constant power without actually being used.

**UPDATE 2:** Success, see below:

**UPDATE 3: **I'm not quite getting full functionally in the dedicated card (work in  progress) but integrated graphics are currently working much better than  pre-Ironhide.

---

### Post by Trilby on 2011-12-14
I've come across a project for Optimus computers, called Ironhide. I've just installed it and it seems that it brings functionality to the Nvidia card. I've yet to work out how well it manages power and switching between high/low performance, but for the moment, I'm calling this fixed.

```

sudo add-apt-repository [B]ppa:mj-casalogic/ironhide
[/B]sudo apt-get install ironhide
ironhide-configuration
```
**EDIT 1:** Oh, I forgot: Look at [https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux") for a discussion of Ironhide and the other available projects.

**EDIT 2:** I'm not quite getting full functionally in the dedicated card (work in progress) but integrated graphics are currently working much better than pre-Ironhide.

---

### Post by Lekensteyn on 2012-01-20
For automatic Power Management, install Bumblebee 3.0 (which replaces Ironhide). 
See also [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)

---

