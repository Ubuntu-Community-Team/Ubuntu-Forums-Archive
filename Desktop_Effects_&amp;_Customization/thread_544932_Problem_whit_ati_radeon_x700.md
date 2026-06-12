---
title: "Problem whit ati radeon x700"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by niyado on 2007-09-06
i dont speak a lot english but...

well, im having a problem, when i go to system, preferences, desktop effects, gives me an error that says.

[COLOR="Red"]" The Composite extension is not available "[/COLOR]

what can i do in this situation?? im new for linux

i use ubuntu ultimate i think that is the 1.4 the last version, i made all the updates and istall the drivers for the ati radeon x700, i have 512 ram and an intel celeron 3.xx plx need help

---

### Post by smartboyathome on 2007-09-06
try typing compiz --replace in a terminal and tell us what you get.

---

### Post by niyado on 2007-09-06
this is what i write compiz --replace and i get this:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

---

### Post by niyado on 2007-09-07
:(:(:( nop... nothin happen, im even dont know how to know if the ati drivers are installed correctry, i cant even up my resolution more then 1024x768 :( i want to use beryl :(:(

---

### Post by Inxsible on 2007-09-07
have you installed compiz fusion ?

there is a difference between compiz and compiz fusion. the former comes pre installed with feisty. the latter is a merger between compiz and beryl and can do a bunch of cool stuff. try following one of the guides to install compiz fusion

---

### Post by hidden_leaf_sasuke on 2007-09-07
ok..this is the step you should do to use compiz-fusion WITH ATI radeon

1. Install ATI driver.
2. Install XGL
3. Then only you should install Compiz-Fusion.

If you dont do steps above step-by-step, then you cant run compiz-fusion

---

### Post by niyado on 2007-09-07
the last time, i try to modificate the xorg whit a guide that i found, but it occurs an error that crash the entire system so... i up ubuntu again from 0...

ok, this is an image that give me my system,,,

[IMG]http://img237.imageshack.us/img237/6388/screenshotis8.png[/IMG]

i really need help

ati radeon x700 i think that is pci express

---

### Post by spartus4 on 2007-09-08
> **hidden_leaf_sasuke said:**
> ok..this is the step you should do to use compiz-fusion WITH ATI radeon

1. Install ATI driver.
2. Install XGL
3. Then only you should install Compiz-Fusion.

If you dont do steps above step-by-step, then you cant run compiz-fusion

He has the X700 as I do.  He isn't going to want to use XGL.  The open source "radeon" driver works much better and can use AIGLX plus composite.  Trust me I also have a x1650 Pro and I have to use XGL with it and it eats up a lot of CPU time.  XGL is also sluggish.  The x700 with AIGLX is the way to go.

---

### Post by niyado on 2007-09-08
thx im going to chek it out, u think that is a manual here in the forum, im new in this forum:)

---

### Post by niyado on 2007-09-08
i want to know if this guide will help me:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by spartus4 on 2007-09-08
> **niyado said:**
> i want to know if this guide will help me:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

That guide is perfect it is the same one that I used.  I just skipped over the part concerning Beryl.  I used the parts of the other guides to install Compiz Fusion.

---

