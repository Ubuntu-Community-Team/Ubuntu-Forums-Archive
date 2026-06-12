---
title: "No Proprietary Drivers/Desktop effects don't work"
date: 2009-03-25
forum: General Help
---

### Post by dwieeb on 2009-03-25
Hi, I own an EeePC 1000 and it seems that desktop effects including Compiz do not work. I ran a Compiz Check:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

---

When I go to Hardware Drivers it checks for drivers and then says "No Proprietary drivers are in use on this system". I can't find the drivers I need, either.

And I don't know what Software Rasterizer in use means. Can anyone help me?

---

### Post by KCG102282 on 2009-03-25
I seriously doubt you will be able to run compiz with an eeePC

---

### Post by redonwhite on 2009-03-25
> **KCG102282 said:**
> I seriously doubt you will be able to run compiz with an eeePC

I agree.  With an atom n270 i doubt you will be able to get compiz going.

---

### Post by fela on 2009-03-25
Compiz will work on your system as I've installed and run compiz with the desktop cube and all that on a EEE PC 701.

Are all your repositories enabled? Go to System > Administration > Software Sources and make sure all the boxes are ticked. Then (after closing the app), reload your repositories.

You could try searching for the driver in synaptic, I've had lots of problems with the restricted drivers app in the past. I would think that you have an intel integrated graphics card.

Good luck! :)

---

### Post by fela on 2009-03-25
> **redonwhite said:**
> I agree.  With 1gig and an atom n270 i doubt you will be able to get compiz going.

I've run compiz with 256MB, what ya talkin about? :guitar:

---

### Post by dwieeb on 2009-03-25
Hey guys, Thanks for all your replies!

I forgot to mention that desktop effects (including compiz) have worked before on my eeepc, but they stopped working a few months ago.

fela, I see the check boxes but there are quite a few tabs. I don't see anything sticking out but I'm sort of new to Ubuntu.

What do I search for? I don't know which driver I need

---

### Post by dwieeb on 2009-04-02
Herro?

---

