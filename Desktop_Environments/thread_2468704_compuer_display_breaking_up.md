---
title: "compuer display breaking up"
date: 2021-11-08
forum: Desktop Environments
---

### Post by jgw on 2021-11-08
I thought I had this beat - I was wrong.  My display will sometimes start flashing my display or breaking it into a mess.  The good thing is that it doesn't last long.  This is my display card (from inxi -Fxz):
  Device-1: NVIDIA G84 [GeForce 8600 GT] driver: nouveau v: kernel 
  bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.11 driver: none resolution: 1920x1080~60Hz 
  OpenGL: renderer: NV84 v: 3.3 Mesa 21.0.3 direct render: Yes 

I also have a nvidia driver: X.org, X server - Nouveau display driver.

I tried to switch to the Nouveau display driver which gave me that black screen of death so I swapped back to what I have now (posted that one).  I have no idea what to do next and I can live with what I have if I have to.

Thank you......................

---

### Post by Autodave on 2021-11-08
I doubt that this is your problem, but I actually saw this today.......a wired keyboard!  Doing pretty much like you are describing.  They swapped the keyboard and problem solved.  I had them hookup the old keyboard and saw it for myself.  Weird.

---

### Post by rsteinmetz70112 on 2021-11-10
I've had similar problems with nouveau but different chipsets. I haven't found a solution I avoid the dm that caause the problem. Someday I'm going to work through it and  figure out what works and what doesn't.

---

### Post by jgw on 2021-11-10
Thanks for the replies

I just swapped out my keyboard.  Since it doesn't go nuts all the time I will see what happens.  I am on a kvn - so far so good, I will see what happens

I may have to just live with it.  I tried nvidia (340) and got the black screen.  I have a couple other cards I think I will swap them out and see what happens.

Anyway - thanks again!

---

### Post by jgw on 2021-11-11
changing the keyboarfd did nothing (tried a couple of them)  Haven't swapped out the display card yet.

---

### Post by Autodave on 2021-11-11
Check connections first: internal and external.  While you have the cover off, what do the cooling fans look like?  Are they dirty / plugged?  Are they all working?

---

### Post by jgw on 2021-11-13
swapped out the display card and that may have helped a bit but still getting strange stuff, just not as much.  All the fans, etc. are working just fine and its all clean inside.

I will just keep on thinking on what to do next.  I have some other cards (all nvidia) which I can try but it doesn't look like that's the problem

---

### Post by jgw on 2021-11-16
I have also noticed that when I boot up in the morning firefox also automatically opens, along with some other stuff.  When Firefox, and some other stuff, displays its all squished down to half the height of the screen.  If I then run settings it fixes itself and then those that are supposed to cover the screen do cover the screen.  My resolution is 1920x1080

Now its sometimes its squished and sometimes not.  I am tempted to use the nvidia 340.108 but the last time I got the black screen of death.

---

