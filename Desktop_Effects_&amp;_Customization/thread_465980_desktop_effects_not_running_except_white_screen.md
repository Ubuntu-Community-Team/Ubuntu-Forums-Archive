---
title: "desktop effects not running except white screen"
date: 2007-06-06
forum: Desktop Effects &amp; Customization
---

### Post by sreenivas1234 on 2007-06-06
hi, 

am pretty new to linux, to day i got eubunty cd and i installed in hard drive, as soon as i installed i wanted to activate the desktop effect, but when i click to activate WHITE BLANK SCREEN WILL appears and when i press escape or double click mouse it vanishes

my system configuration

HP desktop d220

X86 based pc
Pentium 4
mother board inter i845 GV
RAM: 512 +256 DDR in two slots

integrated graphic card of 64 MB memory

can any body tell me how can i use this
thanking you

---

### Post by kaputstyle on 2007-06-06
Check your video card, my integrated video card wasn't good enough.  I found a radeon 7000 in my parts box, and I plugged it in... The enhanced desktop worked fine however i had much more problems when trying to run xserver and beryl.  But for the basic desktop features it worked.  My suggestion:  try another video card.

---

### Post by ggaaron on 2007-06-06
You probably don't have acceleration on - what does
```
glxinfo | grep -i rendering
```
tell you?

---

### Post by Orochi on 2007-06-06
I have this same problem.

I'm running on a Sony Vaio laptop VGN-T170P
Centrino  1 Ghz
1 MB RAM
Intel integrated graphics (855GM)

The output of my glxinfo is
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

```

This Intel card in general is nothing but trouble. It has resolution issues, and leaves visible trails when moving windows around. Perhaps the problem is that the chip hasn't been allocated enough memory from the RAM? (since it has no memory of its own). Is there a way to change how much RAM is allocated to the graphics chip?

---

### Post by Error47 on 2007-06-06
I have the same problem, only with no errors. It just doesn't work, I wouldn't be surprised, my graphics cars is one of the worst. 

And it looks like I have an SIS Si7012 or a SiS962
I am looking at the device manger, it's one of those.

---

### Post by ggaaron on 2007-06-07
Maybe you use intel driver - I had same issues with this driver - use i810 instead, and set proper video ram for your card (but it's only speed improvement, even without this it should work).

Run:
sudo dpkg-reconfigure xserver-xorg

and choose i810 as driver and when it asks about which modules to load, check every one of them.

Worked for my i915 and i945 cards.

---

### Post by ggaaron on 2007-06-07
> **Error47 said:**
> I have the same problem, only with no errors. It just doesn't work, I wouldn't be surprised, my graphics cars is one of the worst. 

And it looks like I have an SIS Si7012 or a SiS962
I am looking at the device manger, it's one of those.

lspci will tell you what is it.
But I believe that beryl only "works" (its still unstable) for radeon, intel and nvidia cards.

---

