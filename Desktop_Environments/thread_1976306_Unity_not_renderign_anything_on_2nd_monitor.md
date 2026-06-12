---
title: "Unity not renderign anything on 2nd monitor?"
date: 2012-05-08
forum: Desktop Environments
---

### Post by Jynks on 2012-05-08
Hi

I'm trying to get 3 monitors running. I can get them running using the "twinview" but I am trying to get them running with separate X Windows so I can have a unique cube on each monitor. 

I have a main monitor and a 2ndary monitor and a  Cintiq Wacom. The wacom is really a "computer" in stelf that I use for painting and this is why I need the unique cubes.

Now I have the x-windows working fine it seam though the nvidia control panel.. but unity is just not rendering anything on the screens at all. It shows as completely white, but I can drag my mouse over and it is a big X... if I go into "advanced setting" and disable the desktop the screen gose black and I can still move my mouse over to the other monitor. 

So it "looks" to me as if I have the drivers working correctly but unity itself is just not rendering anything on the 2ndary monitors... do you know any way I can do this?

---

### Post by Favux on 2012-05-08
Hi Jynks,

What video chipset do you have?
```
lspci | grep VGA
```
If you have installed a poprietary driver for it do you have the monitors set up through the configuration gui that comes with it?  If so what do you have things set at?

Once they are working you should be able to use the Wacom Graphics Tablet applet in System Settings to place your stylus on the correct monitor.

---

### Post by Jynks on 2012-05-08
um... forget about the wacom table for now....

what is happening is that the new 2nd and 3rd monitors are showing all white screens with no windowing on them... if you disable the desktop they go black.. you can not interact with the screen at all apart from dragging your mouse there... it is as if unity does not load on the 2nd and 3rd screen.

I set up the monitors using the nvidia settings thing. They are set to "separate X Windows" as this is the only option that has the functionality I need.

Basically the monitors themselves are working fine.. duel screen and all that.. hardware wise... the problem is that unity itself is not displaying or drawing or w/e the term is on this 2nd monitor.

---

