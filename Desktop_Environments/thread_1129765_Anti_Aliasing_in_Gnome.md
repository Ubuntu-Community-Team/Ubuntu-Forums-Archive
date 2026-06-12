---
title: "Anti Aliasing in Gnome?"
date: 2009-04-19
forum: Desktop Environments
---

### Post by jibsta on 2009-04-19
Hi how can I get gnome to anti alias the 3d effects, they look so ghetto with jaggies everywhere....

If this was answered sorry, every search just brought up text smoothing.

---

### Post by inobe on 2009-04-19
you can do this in nvidia-settings or ati control panel.

example: [IMG]http://www.itsyourpc.org/duane/files/anti.jpg[/IMG]

i hope my suggestions help

---

### Post by jibsta on 2009-04-19
I have all those settings maxed, they apply to any 3d apps running but not to the enivroment itself.

---

### Post by inobe on 2009-04-19
jibsta the 180.44 driver has a crap load of fixes, i update and there hasn't been a hiccup with desktop affects.

my desk use to crash with the cube using 177's

---

### Post by jibsta on 2009-04-19
Im running the 180.44, they are stable and everything works great but all the 3d stuff is jaggy ....

---

### Post by inobe on 2009-04-19
did you install anything other than the default affects manager.

how do you have the affects setup.

i am not experiencing what your describing.

---

### Post by jibsta on 2009-04-19
Using the default or compiz makes no differencs it seems to me the hardware accel is not using the anti aliasing...

---

### Post by inobe on 2009-04-19
this is the best i can come up with jibsta

[http://brainstorm.ubuntu.com/idea/505/](http://brainstorm.ubuntu.com/idea/505/)


obviously it's still some sort of nvidia issue, someone did post instructions about reseting compiz.

hope it works out for you

---

### Post by jibsta on 2009-04-19
AHH solved it, had to switch from enhance to force and restart everything...

---

### Post by inobe on 2009-04-19
that's excellent jibsta i am glad it worked for you.

we really appreciate disclosing how you solved the problem, i certainly hope i helped too.

---

### Post by jibsta on 2009-04-19
THanks for the hekp, I think this option should be built into the program and not have to be forced by the nvidia drivers....

---

### Post by jibsta on 2009-04-19
The link you sent me, I originally had the drivers in enhance app settings, i switched them to override app settings but never thought to restart compiz, once i restarted that and the basic desktop effects, everything is smooth as a babys *** :)

---

### Post by inobe on 2009-04-19
> **inobe said:**
> that's excellent jibsta i am glad it worked for you.

we really appreciate disclosing how you solved the problem, i certainly hope i helped too.

you may have missed my post, i quoted myself.


and your welcome.

---

### Post by jibsta on 2009-04-19
> **inobe said:**
> you may have missed my post, i quoted myself.


and your welcome.

Just saw it and answered it above.

The link you sent me, I originally had the drivers in enhance app settings, i switched them to override app settings but never thought to restart compiz, once i restarted that and the basic desktop effects, everything is smooth as a babys ***

---

### Post by inobe on 2009-04-19
if your nvidia settings don't stick after a reboot' you may need to access nvidia-settings with higher privileges to make them stick.

in terminal do

```
gksu nvidia-settings
```

apply settings and no more worries, just be careful in there.

---

### Post by jibsta on 2009-04-19
Ok thanks, one headsup i notice tho, with 16 AA on, my card is staying in full power and not throttling down so if your caring about fan noise or battery life on a laptop this is probably a bad idea.

---

### Post by inobe on 2009-04-19
i will agree with you on that, this will heat up the gpu and draw power, good point jibsta.

in fact i don't think this would be recommended for anything under 6xxx series nvidia card :)

---

