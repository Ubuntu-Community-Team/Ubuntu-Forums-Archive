---
title: "Cant change Screen resolution..."
date: 2009-04-26
forum: General Help
---

### Post by sports fan Matt on 2009-04-26
I cant seem to adjust my screen resolution..In System>Adminstration there isnt an option to change the screen resolution..I upgraded from 8.10 the last time..and im running a  Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop ..Any Ideas?

---

### Post by sports fan Matt on 2009-04-26
the problem has worsened...I now cannot boot Jaunty and it says "your screen settings have been placed back to defaults"  Any ideas?  I dont want to clean install unless its absolutely necessacary..:)

---

### Post by hansdown on 2009-04-26
Hi sox fan Matt.

I think it has been changed to "display".

System> preferences> display.

---

### Post by sports fan Matt on 2009-04-26
ok..but I now cannot boot into jaunty...the screen resolution is mucked and im trying to figure out how to fix it so I can at least boot into it to fix the resolution..any ideas?..I did a mistake by installing nividia drivers (I didnt realize I didnt need them) and now I cannot boot...

---

### Post by hansdown on 2009-04-26
Ouch. I'm still using 8.04, so my advice isn't worth much.

Can you boot into safe graphics mode?

Try F2 when you boot up.

---

### Post by sports fan Matt on 2009-04-26
I can try..but then what? sudo dpkg-reconfigure xserver-xorg?

---

### Post by sports fan Matt on 2009-04-26
that command actually drops me into my lenovo settings..is it better to reinstall, from intrepid>jaunty?  I am at a loss...

---

### Post by spiderbatdad on 2009-04-26
hey sox fan matt.
maybe try the "xforcevesa" added to the kernel boot line...press e to edit then move to the kernel line with arrow key. press e again, delete quiet splash and add the option to the end of the line. hit enter, press b to boot.

---

### Post by sports fan Matt on 2009-04-26
Since that refused to work, i'll just reinstall 9.04 from 8.10...Its alot less hassle plus its pouring rain here and not a good day to be outside...

---

### Post by sports fan Matt on 2009-04-26
I did try to xforcevesa and the screen resolution was still mangled ...I appreciate all who attempted to help....

---

### Post by doccolinni on 2009-04-26
> **sox fan Matt said:**
> I cant seem to adjust my screen resolution..In System>Adminstration there isnt an option to change the screen resolution..

That's because it's not under Administration, you should be able to change the screen resolution in System -> Preferences -> Display.

I don't know what to do now that you can't even boot it up, though. :confused:

---

### Post by sports fan Matt on 2009-04-26
If i could boot, I could =) ..Im not sure why I cant...

---

### Post by spiderbatdad on 2009-04-26
if you havent began your re-install yet...you could try setting a vga resolution instead of xforcevesa.```
vga=792
```at end of kernel line.

---

### Post by sports fan Matt on 2009-04-26
ahh i started it...its ok though cause everything i have is backed up so it wont take me long when i get to jaunty to reinstall everything...

---

### Post by sports fan Matt on 2009-04-26
Finally back to jaunty :)

---

