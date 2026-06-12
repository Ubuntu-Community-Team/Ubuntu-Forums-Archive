---
title: "Compiz effects hiccups (temporary framerate drop), especially cube"
date: 2009-11-11
forum: Desktop Environments
---

### Post by sheekeebut on 2009-11-11
Hello all,

Using 9.04 Jaunty 64 bit 
Video Card: NVIDIA GeForce GTS 250 with 1 GB video memory.
System: Intel Core 2 Quad 2.5GHz Q8300,4 GB DDR 2, Asus P5QL SE board.
If you really need more hardware info, just ask. I doubt that it's strictly hardware-related, however.

I run Compiz Fusion (awesome desktop, by the way), and with Emerald because I totally had to have the window decoration blur. Newb as I am, everything on my system has been installed from Synaptic, INCLUDING the nvidia drivers and compiz version.



I have the Compiz Cube enabled. The framerate drops (to around 5-10 fps) for about 2 or 3 seconds when I begin doing either of the following:

-switching desktops with Rotate Cube (like mouse rotate, moving a window to another desktop or simply switching desktops with ctrl-alt-left / right)
-moving Wobbly Windows around

After those initial 2 or 3 seconds, it goes back to the silky smooth framerate that I love. The only problem is, I notice that after about a minute of not using any of these effects, I know I will face this problem again. 



I have already tried all sorts of combinations of the following settings:

(1)
$ export __GL_YIELD="NOTHING"; compiz --replace

(2)
all four combinations of the two settings from the Compiz Fusion Icon:
-loose bindings
-indirect rendering
(in fact, it's strange that when I start Compiz Fusion Icon from Applications>System Tools, loose bindings is unticked, and the cube animates smoothly, then if I tick it once, it still stays smooth, but when I untick it again, framerate remains constantly low at around 2-3 fps, and I restart the computer just to get it back to what it was [or tick loose bindings again])

(3)
turning off all the following Compiz effects that I normally use (found in the Effects section of CCSM):
-Reflection
-Blur Windows
-Wobbly Windows
-Animations
-Cube Reflections and Deformation (I've also tried changing the shape of the cube from cylinder to cube to sphere)

(4)
turning off Emerald

I'll keep you all posted on any other clues I may find.

---

### Post by Dullstar on 2009-11-11
There is a command that can check for compiz compatibility.

I don't remember what it is though.  In the meantime, try this.
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=HK7&ei=LJL7Ss7WLITEnge3x6yNBQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=compiz+compatibility+check+command+ubuntu&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=HK7&ei=LJL7Ss7WLITEnge3x6yNBQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=compiz+compatibility+check+command+ubuntu&spell=1)

---

### Post by sheekeebut on 2009-11-12
If you're referring to the compiz-check script, which I've found through your link, I've just tried the test, and it's all green [COLOR=Green]**OK**[/COLOR]s.

I really don't think there's a compatibility issue here, considering that after the few seconds or so it returns to its smooth animation. I haven't seen Compiz Fusion crash or give me any errors, either.

As mentioned before, I've also tried:

$ export __GL_YIELD="NOTHING"; compiz --replace

I know that you have to use <export> to set an environment variable, but how can one know that it's taken effect?

---

### Post by sheekeebut on 2009-11-12
Hey, I think I've figured it out. This performance problem relates to nvidia's Powermizer function. I realized that the bad framerate happens when the Performance level drops to 0, severely lowering the NV and memory clocks, hence the bad performance after 2-3 minutes of mouse inactivity.  This would happen quite often because Powermizer kept on dropping the level.

I searched it up by googling:

ubuntu disable powermizer

To make a long story short, I created a file called options.conf in /etc/modprobe.d/
with the following:

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
options nvidia NVreg_Mobile=1

Now it's always set to performance level 1, and it's smooth sailing from here on in.

Thanks for the help!

---

