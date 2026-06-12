---
title: "dell latitude d830 i8kctl fan error"
date: 2009-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtrmplayr on 2009-08-21
Hi, I have Ubuntu Jaunty installed on a Dell Latitude D830. Because my computer runs uncomfortably hot, I want to force the fans to run on max all the time. One way I got Ubuntu to do this was through the command "i8kctl fan - 2". When I run this command, the fans  rotates at maximum speed, but only for a moment. The fan speeds always reverts back to its original, slower speed almost immediately after I use this command. Is there a way to make the fans spin at max speed all the time? I've tried lm-sensors to control the fan speed, but it doesn't detect my fans. I've also tried dellfand, but it also experiences the same problem as i8kctl. Something always slows down the fans. As a result, the fan makes a pulsing noise as  i8kctl/dellfand speeds up the fan, and something else slows it down.

= = = = =
[I]In case someone finds the thread: In a fresh install of 14.10 the fan runs silently and is only speeding up under heavy work load. 

Mörgæs 2014-12-19[/I]

---

### Post by BryanFRitt on 2011-06-15
Did you ever figure this out? It's not working on my Dell Latitude D830 either.  

p.s. Dell Latitude D830 isn't listed in i8kfan Compatibility list. As far as I know D830 is fairly similar to D820. 

[http://www.diefer.de/i8kfan/](http://www.diefer.de/i8kfan/)
-
Here's what I've done.

after installing i8kutils I got
 * Not starting. Disabled via /etc/default/i8kmon.
 * Not starting. Disabled via /etc/default/i8kbuttons.
edit those file and set to enable (read what it says inside the file)
sudo modprobe i8k
i8kctl fan - 2

results: same problem as yours, fan speed up for 1 second and then goes back down.

---

