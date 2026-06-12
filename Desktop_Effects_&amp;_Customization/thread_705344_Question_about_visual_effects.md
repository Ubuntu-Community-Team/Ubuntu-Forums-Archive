---
title: "Question about visual effects"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by y0umebednow on 2008-02-23
Alright so im using ubuntu 7.10 and i have installed my video drivers for P4M800PRO chipset.
i have also installed Compiz (Advanced desktop effects setting).
My question is that why can't i get visual effects to work?
is it because my onboard video is crap?
or am i missing something?

i mean i uncheck all the checked boxes in CompizConfig setting manager but still it gives me the error that Desktop effects could not be enabled.

Any Ideas? im a total noob with linux. Friend told me to try it

---

### Post by luisromangz on 2008-02-23
Yes, the most probable reason is that your integrated video card is crap. Do yo have 3D acceleration with it?

---

### Post by y0umebednow on 2008-02-23
not sure what that is. wanna explain please lol

---

### Post by carlos2k8 on 2008-02-23
I have the same problem, diff motherboard, but mine has 3D accelleration, but whenever I click on system > preferences > appearance > visual effects, I click normal / extra and it says "desktop effects could not be enabled"

---

### Post by luisromangz on 2008-02-24
If your video card is working with 3D applications correctly, then you have the 3D acceleration support enabled. That's is needed by compiz, but compiz also needs special support to be offered by the drivers. Nvidia, ATI and Intel graphics cards (usually) works, but it doesn't mean that all video graphics adapters, including those integrated, should work.

---

### Post by rohedin on 2008-02-24
Run* glxgears *from the terminal, does that work OK?

---

### Post by y0umebednow on 2008-02-24
yeah it does, but it is a little slow. 
its like my visualizations in rythembox, also slow

---

### Post by Kubotaz4 on 2008-02-24
I had similar problems, but got them fixed
 go to -applications
          -add/remove
          -search for "envy"
         -follow the guide

it helped me, so im passing on some knowledge!

---

### Post by y0umebednow on 2008-02-24
envy24 control? in the description it says it has do with sound hardware..?

well anyways i installed it, now what is the guide you talk about?

---

### Post by y0umebednow on 2008-02-24
ok nvm that...
i installed the new envy from the web.
got everything to work
but when i choose to install nvidia or ati drivers, it says There was an error in the installation process. You can see the log file /var/log/envy-installer.log

---

