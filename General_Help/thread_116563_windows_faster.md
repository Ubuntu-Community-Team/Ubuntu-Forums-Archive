---
title: "windows faster"
date: 2006-01-13
forum: General Help
---

### Post by phidippus on 2006-01-13
I ran the exact same program on Netlogo (java) and found that it runs much faster on windows xp (not just a little bit faster). Does this mean my ubuntu is configured bad, or is this something I should expect?

---

### Post by Sef on 2006-01-13
From Netlogo's site:

> My model runs slowly. How can I speed it up?

Here's some ways to make it run faster without changing the code: 
Edit the forever buttons in your model and turn off the "Force view update after each run" checkbox. This allows the view to skip frames, which may speed up models which are graphics-intensive. (See the Buttons section of the Programming Guide for a discussion of this.) 
Use the freeze switch in the view control strip, or the no-display command, to freeze the view temporarily. For example: 

to go
  no-display
  ...
  ...
  display
end
If you use this technique, you should turn off the "Force view update" checkbox, since the display command already forces a view update. 
If your model is using all available RAM on your computer, then installing more RAM should help. If your hard drive makes a lot of noise while your model is running, you probably need more RAM. 
Use turtle size 1, 1.5, or 2 as these sizes are cached by NetLogo. 

In many cases, though, if you want your model to run faster, you may need to make some changes to the code. Usually the most obvious opportunity for speedup is that you're doing too many computations that involve all the turtles or all the patches. Often this can be reduced by reworking the model so that it does less computation per time step. If you need help with this, if you contact us at [email]feedback@ccl.northwestern.edu[/email] we may be able to help if you can send us your model or give us some idea of how it works. The members of the NetLogo Users Group may be able to help as well.

Link: [http://ccl.northwestern.edu/netlogo/]("http://ccl.northwestern.edu/netlogo/")

---

### Post by phidippus on 2006-01-13
Thanks. This made the simulations as fast as running it on windows, but I'm satisfied with this speed. It's fast enough (for now). :)

---

### Post by dcstar on 2006-01-13
[QUOTE=phidippus]Thanks. This made the simulations as fast as running it on windows, but I'm satisfied with this speed. It's fast enough (for now). :)[/QUOTE]
And if it is a graphics intensive app, if your Ubuntu install doesn't have specific video drivers with acceleration enabled, then that may also be a factor (Windows is more likely to have this working - unfortunately).

---

### Post by phidippus on 2006-01-13
My Video card is nvidia. How do I check if the system is correctly recognizing it?

---

### Post by phidippus on 2006-01-13
I looked xorg.conf and found

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce Go 6600 TE/6200 TE]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Does this mean the reason it is slow is not because of graphic card?

---

### Post by JimS on 2006-01-13
...

Don't expect that a Windows developed HW
will run as well in Linux as in Windows.  DON'T.

If you are lucky it may run well, but that is like
putting a Ford engine in a VW.  You may need
some expertize, specialized parts, a bit of cutting,
and some welding.

I did put a Ford V6 in the back of a VW van.
It worked, but it never worked well in all situations.
I was forever stopping and fixing something.
Expect the same when using Windows gear
with a Linux OS.

This is not to say you shouldn't try using Windows
HW in your Linux OS driven box.  But don't get
your expectations unreasonally high.  You may
get lucky.  You may crash.

Good Luck,

JimS
Prostate Cancer Aware
...

---

