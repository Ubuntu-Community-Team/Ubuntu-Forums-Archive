---
title: "Impossible to start compiz on my system?"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by themess on 2007-07-07
Okay, so I'm really new to Ubuntu but I thought I'd give it a shot solely because of compiz fusion. So far I've managed to install compiz fusion with out a hitch but after installation it told me that compiz couldn't run using vesa drivers. I installed Envy and got my Nvidia drivers working, again without a hitch. After restarting and trying "compiz --replace" I get the following message.

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

I have no idea what to do, I searched around for a while but to no avail. Please help me get this going, I don't want to go crawling back to Vista.

Thanks.

---

### Post by Happy_Man on 2007-07-07
Um, it appears that your video card may be too old or too new to support the Nvidia linux drivers. Try the Ubuntu drivers.

---

### Post by LouisvilleLIP on 2007-07-07
I'm certainly not an expert, but I got that same message on my ATI card, and it works just fine.  I think it had to do with XGL, but I can't remember now.  Anyway, keep looking, it might not be hopeless.

---

### Post by themess on 2007-07-08
My video card is an 8600m GS. I guess that could be too new... How would I go about installing ubuntu drivers? I had to use the alternative installation disc to install ubuntu. Then i had to reconfigure xserver to install the vesa driver. Would I install this ubuntu driver the same way?

---

### Post by Happy_Man on 2007-07-08
> **themess said:**
> My video card is an 8600m GS. I guess that could be too new... How would I go about installing ubuntu drivers? I had to use the alternative installation disc to install ubuntu. Then i had to reconfigure xserver to install the vesa driver. Would I install this ubuntu driver the same way?
No, If you are on Feisty, all you must do is go to System --> Admininstration --> Restricted Drivers Manager, and install from there. It's all automatic.

---

