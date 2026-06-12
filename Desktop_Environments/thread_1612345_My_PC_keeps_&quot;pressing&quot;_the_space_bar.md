---
title: "My PC keeps &quot;pressing&quot; the space bar"
date: 2010-11-03
forum: Desktop Environments
---

### Post by potatan on 2010-11-03
Hi,

Since yesterday, my PC has started occasionally generating lots of spacebar presses, as if something is resting on the keyboard.  I have tried a second PS/2 keyboard in place of the USB one and the problem persists (so it is probably not a hardware issue). 

The only significant change to my PC is that I installed a few webcam programs a couple of days ago (Motion, Stopmotion, Zoneminder plus dependencies) so maybe this has done something odd?  I have uninstalled the apps now.

Any ideas? Or any way of tracing interrupts or something to help diagnose this problem?

Thanks in Advance.

---

### Post by P4man on 2010-11-03
You could have a look at the output of dmesg if that shows anything. Or you could open a terminal and run

xev

Then put your mouse in the white box and see if xev catches any mysterious spacebar presses?

---

### Post by pokerpokie on 2010-11-03
It's a ghost? lol

---

