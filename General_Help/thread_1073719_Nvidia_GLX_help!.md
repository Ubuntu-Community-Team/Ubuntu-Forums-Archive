---
title: "Nvidia GLX help!"
date: 2009-02-18
forum: General Help
---

### Post by xX-Felipao-Xx on 2009-02-18
Hi !
I'm using ubuntu Intrepid Ibex, and I "successfully" installed nvidia 173.14.12 drivers through EnvyNG.

But look at the screenshot: There's no GLX !

I read in envy's creator blog that in Intrepid the nvidia-glx-envy-new packages have been replaced by nvidia-glx-VERSION packages, which I found in Synaptic and installed nvidia-glx-173 then. Still not working...

I'm having problems for 5 days, since I tryied to update to 180.XX driver versions... (I don't wanna do this now, goodbye 180.xx) 

Thanks in advance ;)

---

### Post by xX-Felipao-Xx on 2009-02-18
BUMP!

Help neeeded!! :(

---

### Post by xX-Felipao-Xx on 2009-02-19
Bump :/

---

### Post by xX-Felipao-Xx on 2009-02-19
Bump!

---

### Post by fragos on 2009-02-19
Your problem is a mystery to me. My FX5200 card uses the same driver and direct rendering is supported. It was not necessary to run Envy and that may indeed be part of your problem. What does Hardware Drivers Preferences say. In my case versions 96 and 173 were offered automatically and I had to select and activate the one I wanted to use. You haven't mentioned which Nvidia card you have and that could be part of the problem as well.

---

### Post by xX-Felipao-Xx on 2009-02-19
Well, Hardware Drivers says the same as you, and I have selected the 173 one !

My card is a FX5200 too... so weird...

---

### Post by solwic on 2009-02-19
> **xX-Felipao-Xx said:**
> Well, Hardware Drivers says the same as you, and I have selected the 173 one !

My card is a FX5200 too... so weird...

It offered me 173 or 177.  I opted for 180, which fixes a lot of the problems I was having.  

The only option in your hardware drivers list is 173?

---

### Post by xX-Felipao-Xx on 2009-02-19
No, i have to chose between 173 and 96. (both were installed by envyng)
Which is your card? Because I have some doubts about if 180 drivers fit with my card...

edit: hmmm, wait, in the first part:

> It offered me 173 or 177. I opted for 180, which fixes a lot of the problems I was having. 
If that is in Envy, I had up to 177, which said it wasn't neither compatible nor recomendable.

---

### Post by xX-Felipao-Xx on 2009-02-20
Bump again :S

---

### Post by fragos on 2009-02-20
Ubuntu's main, universe aand multiverse repositories reflect a degree of confidence and support. Main has the best support and stability. This is not to say that something in multiverse is of poor quality but it does reflect the distrobution authors haven't sufficiently tested and verified the packages to offer support. The OP has selected to use a non-standard method of installing Nvidia drivers. My recommendation is to attempt to undo envy and utilize the standard methos of driver installation.

---

### Post by xX-Felipao-Xx on 2009-02-20
Its ok if I understand by undo, uninstalling every package related with envy and nvidia I see in Synaptic? Or there's any step lacking?

---

### Post by fragos on 2009-02-20
I'd uninstall the envy stuff. Packages marked with the Ubuntu logo are OK. I'd mark nvidia-glx-173 for install or reinstall -- I believe it's the driver you want. You should probably also make sure that this driver is selected in Hardware Driver Preferences. Respond to this thread with your results. There may be more we need to do as I'm unsure on what envy changed in your system.

---

### Post by xX-Felipao-Xx on 2009-02-20
OMG ! Hardware Drivers is gone !
And its not hidden, I've checked in the Menu Editor...

This isn't good

---

### Post by fragos on 2009-02-20
The only suggestion I can make is to backup your data do a clean install.

---

