---
title: "desktop effects"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by digtal_chocolate on 2007-06-17
anyone with extensive knowledge of ubuntu please help me configure the desktop effects. I have a hp pavilion a510n with an integrated 64 bit  video card and I'm not sure if this computer is able to handle the effects. It's completely standard and runs ubuntu fine, but gives an error message when I try to enable the efffects. I'm not completely familiar with linux and need a little help. If anyone has the time, I really need the help. I don't wanna run windows anyomre. Thank you

---

### Post by digtal_chocolate on 2007-06-17
anyone with extensive knowledge of ubuntu fiesty 7.04 please help me configure the desktop effects. I have a hp pavilion a510n with an integrated 64 bit  video card and I'm not sure if this computer is able to handle the effects. It's completely standard and runs ubuntu fine, but gives an error message when I try to enable the efffects. I'm not completely familiar with linux and need a little help. My friend runs ubuntu feisty and I absolutely love the cube effects. If anyone has the time, I really need the help. I don't wanna run windows anymore. Thank you

---

### Post by NfF on 2007-06-17
Maybe it's the way your system tells u that the desktop effects could affect your pc performance.
Also desktop effects it's not that advisable,unless u have a fast processor, good Ram memory and a better graphics like the Nvidia graphics card?

Hope this solves ur problem.

---

### Post by Ozeuss on 2007-06-17
you'll have to be more specific as in which error it outputs, what graphics card you're using, and if you followed any howto/tutorial thus far.

---

### Post by waggygee on 2007-06-17
> **digtal_chocolate said:**
> anyone with extensive knowledge of ubuntu fiesty 7.04 please help me configure the desktop effects. I have a hp pavilion a510n with an integrated 64 bit  video card and I'm not sure if this computer is able to handle the effects. It's completely standard and runs ubuntu fine, but gives an error message when I try to enable the efffects. I'm not completely familiar with linux and need a little help. My friend runs ubuntu feisty and I absolutely love the cube effects. If anyone has the time, I really need the help. I don't wanna run windows anymore. Thank you

Ill need to know what graphic card you got.... ATI or Nvidia... they use different drivers

---

### Post by waggygee on 2007-06-17
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) this is should help to setup the ATI driver

For Nvidia driver this command should do the trick:

 sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals

this just sets the drivers, next you'll need Beryl or something to realy enjoy

---

### Post by bapoumba on 2007-06-17
@ digtal_chocolate: both your thread had anwers, I merged them.

---

### Post by Irti on 2007-06-17
64 bit card......hmmmmmmmmmmm.......if u have an nvidea card then just look in the restricted drivers in your system->administration->restricted drivers manager.........if you are using an ati card then you wil have to follow up one of the how to's on ati (look in the tutorial section...)some common desktop effects you can use are screenlets or desklets or you can use the avant-windows navigator or kibadock.........i dont know if you can use beryl though...give it a try..........

---

