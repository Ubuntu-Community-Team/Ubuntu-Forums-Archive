---
title: "no video driver compatible"
date: 2007-11-05
forum: Dell  Ubuntu Support
---

### Post by spayced on 2007-11-05
I'm running Dell Dimension 4700C with a ATI Radeon x300 video card.

I updated to 7.10 and everytime I restart i get "ubuntu is running in low graphics mode because it could not find a compatible video driver" message. Which is obvious, because it struggles to render a web page.  Its not gutsy's fault, ive had trouble with the video card for every ubuntu release. 

I have tried all the ati and radeon drivers on the screens and graphics list. I can't use the one from ATI website because my screen resolution isn't high enough to see the 'next' button. For reals, very frustrating. Anybody have any ideas? My ubuntu is nearly useless at this point, so I'm willing to risk destroying it.

---

### Post by dacap06 on 2007-11-07
When I looked up the Dell Dimension 4700C, I saw it was using the Intel 915 chip set and lists the Graphics controller as the Intel GMA 900.  Presumably you added the ATI card afterwards?  Well regardless, the 915 chipset implements graphics capability in a non-standard way.

Take a look at the 915resolution package in the Ubuntu archives.  It provides different, and far more useful X-windows resolution settings by changing the copy of 915 BIOS in memory (but not the original chip).  Read the notes in the package.  Installing it and making the associated init script changes could be the answer to your problem.  I can't say it is definitely the solution because you added the ATI card to the mix, but it is worth a try.

DaCAP

---

### Post by saru411 on 2007-11-07
have you ever tried using envy to install your graphics drivers? it detects and installs the correct drivers for you. its as easy as point and click.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

i know it says nvidia, but it supports ati also

---

### Post by spayced on 2007-11-08
thanks for the replies,
First I used synaptic to remove every video driver I had. Then I told Envy to setup an ATI driver for me and it worked! I feel dumb for not finding envy earlier. Now OpenGL and larger resolutions work. But I try to enable effects and it says 'desktop effects cannot be enabled.' I'll search through the topics here to find what others did to fix it.

---

