---
title: "My Ubuntu dont load correctly"
date: 2009-04-15
forum: General Help
---

### Post by U-Bom-2 on 2009-04-15
Ok, this is what happen to me when i turn on the computer. I dont know why if i let the Laptop running alone it never load. Thsi happened to me when i upgrade to Ubuntu 8.04

Here is what happen:

1) I push the Power buttom
2) My Toshiba screen appeard with the ESC option and F12
3) Black screen and a text in top-left that said: Crub Loading and something more
4) After that the cowntdown and tell me to press ESC is i want more options
5-A) If i let it say: Starting up please wait... then the text dissapear and the screen stay in black for ever (with lights and all
5-B) If i press ESC it send me to an other screen with 5 options:

Ubuntu 8.04, Kernel 2.6.24-16-generic --- If i choose this it just say the same that 5-A step
Ubuntu 8.04, Kernel 2.6.24-16-generic (recovery mode) --- If i chose this one the PC write a lot of thing scrolling down and after some time it stop on a line that say: [65.511117] sd 4:0:0:0: attache scs: generic sgc type 0
Ubuntu 8.04, Kernel 2.6.22-14-generic --- Here the PC go to step 5-A but after some time Ubuntu load and i can enter and everithing ok
Ubuntu 8.04, Kernel 2.6.22-14-generic (recovery mode) --- like the other recovery mode but it dont stop and present me 3 more options, i just hit enter load some time more and then i load my ubuntu and all is ok

So i want to know if someone can help me because i dont want to be always puching ESC and Enter, i want that my Computer Turnon automatly.

My computer is a Toshiba Satellite L305D-S5892. (laptop)

PS: This happened after i make the upgrade from Ubuntu 7 to Ubuntu 8.

Thanks if someone can help me.

---

### Post by eBoxNet on 2009-04-15
Try to hit alt+ctrl+backspace on your normal boot black screen to check if you get a terminal.

ig you get this then you need to reconfigure your xorg bu running : $ sudo dpkg-reconfigure xserver-xorg

---

### Post by U-Bom-2 on 2009-04-15
> **eBoxNet said:**
> Try to hit alt+ctrl+backspace on your normal boot black screen to check if you get a terminal.

ig you get this then you need to reconfigure your xorg bu running : $ sudo dpkg-reconfigure xserver-xorg

Ok, i will try and then i will post results

---

### Post by U-Bom-2 on 2009-04-15
Nope, nothing. it dont appear nothing.

---

