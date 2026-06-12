---
title: "Now what! Mouse acting all weird"
date: 2007-04-14
forum: Desktop Environments
---

### Post by robenroute on 2007-04-14
Hi there,

Something very odd has just happened: I rebooted my machine (Edgy) and ***(without*** changing my xorg.conf file), my mouse all of a sudden doesn't know what up or down is: the scroll wheel has stopped working. where I could previously scroll up and down through, e.g., web pages (Epiphany, Firefox), text documents (Openoffice.org), etc., scrolling is not possible any longer. Strange thing though: if the content in the window can be scrolled to the right (and subsequently back to the left again), the wheel performs these actions: downward motion becomes scroll to the right, upward goes left.

Anyone? This is so annoying!
Thanks.

P.S.1
Between the working situation and the situation now, I did install the following packages:

comerr-dev (2.1-1.39-1)
libkadm55 (1.4.3-9ubuntu1.2)
libkrb5-dev (1.4.3-9ubuntu1.2)
libneon25-dev (0.25.5.dfsg-5)
libssl-dev (0.9.8b-2ubuntu2)
libxml2-dev (2.6.26.dfsg-2ubuntu4)

I have, just to make sure, removed them again, but to no avails.


P.S.2
The mouse section of my xorg.conf file looks like this (and hasn't been changed, like I said earlier):

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device"              "/dev/input/mice"
    Option         "Protocol"            "ExplorerPS/2"
    Option         "Buttons"             "7"
    Option         "ZAxisMapping"        "6 7"
EndSection

```

---

### Post by ComplexNumber on 2007-04-14
it is probably not anything to do with software. 

on the bottom of your mouse, there should be a 'hatch' where you can open it up and take the ball out. you will notice that the movement of the mouse is controlled by an X and Y wheel sensor that detect the X and Y position and movement of the mouse and then convert that to movement on the screen. i would suggest that its probably the Y co-ordinate wheel sensor that it clogged with dirt. just give it a clean. whilst you're at it, give the ball and the X  wheel sensor a clean too...just in case.


 i assume its that kind of mouse, but the principle is the same anyway.

---

### Post by robenroute on 2007-04-14
Ball? Are ball-based mice still used? My mouse is an Logitech MX400 Laser mouse.... Thanks for the tip though. BTW, it's not the movement of the mouse, it's the scroll wheel!

Anyone else?

---

### Post by ComplexNumber on 2007-04-14
> **robenroute said:**
> Ball? Are ball-based mice still used? My mouse is an Logitech MX400 Laser mouse.... Thanks for the tip though. BTW, it's not the movement of the mouse, it's the scroll wheel!

Anyone else?
well, i still use one.

---

### Post by robenroute on 2007-04-14
> **ComplexNumber said:**
> well, i still use one.

Fair enough! (I was only kidding, as it just sounded so old-fashioned)

But still, I do have a mouse with an identity crisis here. What to do? I'm all ears to people with suggestions.

TIA

---

### Post by ComplexNumber on 2007-04-14
what's about 99.9999999999% certain is that its a hardware problem with your mouse. you say its a laser one, so i bet something has got messed up with it. try wiggling the connection about or something.

if by the 0.00000000001% chance that it is software that is making it perform those funky tricks, i would love to know what its called :lolflag:

---

### Post by robenroute on 2007-04-14
> **ComplexNumber said:**
> what's about 99.9999999999% certain is that its a hardware problem with your mouse. you say its a laser one, so i bet something has got messed up with it. try wiggling the connection about or something.

if by the 0.00000000001% chance that it is software that is making it perform those funky tricks, i would love to know what its called :lolflag:

Please allow me to beat the odds then. When I boot my system from the Feisty (beta) partition, everything works quite all right. And yes, the xorg.conf from Feisty is (as far as the mouse section goes) identical to the Edgy one.

Next one please? ;)

---

### Post by ComplexNumber on 2007-04-14
good job i didn't bet 50 quit on it :mrgreen:. 

maybe someone else has experienced it and knows how to deal with it, or has a suspicion about what it may be.

---

### Post by drlisacuddy on 2007-04-14
> **robenroute said:**
> Please allow me to beat the odds then. When I boot my system from the Feisty (beta) partition, everything works quite all right. And yes, the xorg.conf from Feisty is (as far as the mouse section goes) identical to the Edgy one.

Next one please? ;)

How is it hooked up to the PC? Wired/wireless, USB/PS/2?

100% sure not hardware, since the software controls what a function does to the mouse, not the mouse itself...

---

### Post by robenroute on 2007-04-15
It's prodding the back of the PC case with a PS/2 plug....

---

### Post by robenroute on 2007-04-16
Anyone to help me out here, please?

Thanks

---

### Post by robenroute on 2007-04-17
The problem seems to be solved, although I still need to fathom the reason....

What I did was change the xorg.conf from (old):

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device"              "/dev/input/mice"
    Option         "Protocol"            "ExplorerPS/2"
    Option         "Buttons"             "7"
    Option         "ZAxisMapping"        "6 7"
EndSection

```

to (new):

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device"              "/dev/input/mice"
    Option         "Protocol"            "ExplorerPS/2"
    Option         "Buttons"             "5"
    Option         "ZAxisMapping"        "4 5"
    Option         "ButtonMapping"       "1 2 3 6 7"
EndSection

```

I picked this off the Internet somewhere. But like I said, I don' t understand it....

---

