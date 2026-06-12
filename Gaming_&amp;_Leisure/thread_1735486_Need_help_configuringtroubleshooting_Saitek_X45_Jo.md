---
title: "Need help configuring/troubleshooting Saitek X45 Joystick."
date: 2011-04-21
forum: Gaming &amp; Leisure
---

### Post by MortusEclipse on 2011-04-21
I know it is a rather old joystick and have done considerable searching on the topic but have only found posts from around 2006 when seem not entirely valid any more. I have been playing the game Vendetta Online for a while and wanted to try it with a joystick, as I still had my old X45 by Saitek. So I connected it and most of the buttons and axis's seem to work but the X and Y, the main joystick axis's, the remainder of the functions that don't seem to work are inconsequential at this point.

Is there any steps I may have missed for setting up this joystick in Ubuntu 10.10? If not what is the best way to troubleshoot the joystick and see if the problem is functional and just needs to be replaced? My hopes were really to get this joystick at least functional enough to try it out, and if I liked using the joystick I would upgrade to the X52 which I am pretty certain is supported.

Thanks in advance for any help you can offer.

---

### Post by Linoobius on 2011-05-10
Had the same problem, took me a bit to suss it out but here's what got the stick working for me in Natty.  Make sure you have "joystick" installed, you can find it in the Ubuntu software center, just search for joystick.  Connect your stick and from a terminal window run:

jscal -c /dev/input/js0

It will prompt you to move and confirm with a button press, each of the stick's axis from minimum to center to maximum. Hint, axis 6 and 7 are the hat switch centered above the stick, not the one you have to reach for.  I had to go back and reverse the mapping on those two for them to feel natural in a flightsim but you can experiment.  After that the stick works fine.  Hope you have similar luck.

Linoobius

---

### Post by MortusEclipse on 2011-05-14
Thanks that worked. Do you know of any way to remap the axis from one hat switch to another?

Thanks again.

---

