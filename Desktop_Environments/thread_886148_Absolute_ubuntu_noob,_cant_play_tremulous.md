---
title: "Absolute ubuntu noob, cant play tremulous"
date: 2008-08-10
forum: Desktop Environments
---

### Post by wullto on 2008-08-10
Hi everyone, I installed xubuntu about a week ago on my Inspiron 510m and everything has worked fine. I tried gnome but I figured it was a little to heavy on my old laptop.

So today I tried downloading and installing Alien arena, but when I tried to start the game I got a black screen and then I was back at the desktop. As I have been withouth any gaming for a week now I desperately tried installing Tremulous as well but with the same results.
So I tried googling but I couldn't find a clear answer, but I suspect that maybe my drivers aren't up to date.

Any help would be much appreciated!

PS.Keep in mind that I'm a noobcake please

---

### Post by L815 on 2008-08-11
Do you have compiz enabled? If so try turning it off then playing.

---

### Post by ppc_guy on 2008-08-11
Hey bud,

 Went through the same thing a bit ago. That is an issue with not having the correct video driver installed for you system to utilize opengl. 
 Take a look under SystemTools -> Hardware drivers. There should be a check box there to install the driver for your card. Be it ATi or Nvidia.
 But one thing to consider; depending on the age of the laptop, it might not have enough sharred memory even with the driver to play the game.

 On my thinkpad R40, which is a PM 1.3mhz, 1gig of ram and 64shared ATi card, Alien Arena is barely playable. 

~Nathan

-----------------------------------------------------------------------
As always your mileage may vary.
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
-----------------------------------------------------------------------

---

### Post by wullto on 2008-08-11
Two replies real fast! Thanks alot guys! :guitar:

I couldn't find any checkboxes in Hardware Drivers and I'm not sure wether I have compiz turned on or off. Any ideas?

---

### Post by amadeus266 on 2008-08-11
Try turning compiz off in terminal.```
metacity --replace
``` Then try the game again. If that doesn't work than I would have to agree with the previous post about not enough shared ram.

---

