---
title: "I'm a new epsxe user... I need a few tips"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by D-Unit on 2007-11-01
Hi everyone!  I just downloaded epsxe last night for the sole purpose of playing Castlevania SOTN, at least for now anyways.  I found the game and downloaded it as well, but it runs horribly slow!(this goes for sound and video)  I'm wondering if maybe I have the wrong plug-ins or what.  

System: emachines 1.2 GHz
512 ram
Integrated Intel GPU
80+40 gig HD

Also, the game screen is diplayed on the bottom left hand corner; is this normal?  I will gladly answer any questions anyone has to come up with a solution here.  Oh, and I have the Pete's Open GL video plug-in.

---

### Post by acoustibop on 2007-11-02
Pete does two OpenGL plugins for Linux, D-Unit - however, I'd guess you must be using the MesaGL one rather than the XGL2 one, as the latter likely wouldn't run well, if at all on your card.  Try his PEOpS Soft GPU as well.

ePSXe runs best on lower end machines if there's a fairly pokey videocard to offset the CPU load.  On a system like yours, you might do better to try [pSX]("http://psxemulator.gazaxian.com/") - which, unlike ePSXe and PCSX, is also extremely easy to install and configure in Linux.  Basically, the only extra dependency on a standard Ubuntu install is libgtkglext1, which is in the repositories.

I believe Castlevania SOTN can be problematic on pSX (may be on ePSXe too?) but is usually playable.  See the [pSX official forum]("http://psxemulator.proboards54.com/") for more on this.

---

### Post by NightCrawler03X on 2007-11-16
MesaGL requires decent 3D support in order to work.

One problem might be your graphics card, embedded Intel GPU's are complete garbage, but my brother runs ePSXe quite well on a laptop with such a card, so it probably has to do with your drivers.

Chances are, you have the perfect drivers for your card installed, but none of the libraries required for 3D video acceleration.

Firstly, try;
```

sudo apt-get install libgl1-mesa-dri

```
Then try ePSXe again.


If you are still having problems with 3D acceleration, then do:
```

glxinfo | grep render

```
and
```

lspci

```
Show me the results of typing both these commands.

---

### Post by NightCrawler03X on 2007-11-16
Request:
Can a mod please remove this post? (Not the post above, but the post that you see this text contained within). For some reason, I accidentally posted twice, so I edited this post to inform you of that.

---

