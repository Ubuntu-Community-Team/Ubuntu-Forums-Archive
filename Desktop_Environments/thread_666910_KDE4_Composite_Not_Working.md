---
title: "KDE4 Composite Not Working"
date: 2008-01-13
forum: Desktop Environments
---

### Post by onlineapps on 2008-01-13
Hi,
I installed the libxcomposite1 and libxdamage1 packages on my Gutsy system. Yet when I try to enable Desktop Effects under System Settings > Desktop > Desktop Effects, it says "Compositing is not supported on your system. Required X extensions (XComposite and XDamage) are not available." Do I need to start some fancy Xserver or something?

---

### Post by roach of discord on 2008-01-13
Same problem here. Anyone?

---

### Post by basdi on 2008-01-14
yes i got the same problem


in the tab 'Desktop Effects' it says "Compositing is not supported on your system.   Required X extensions (XComposite and XDamage) are not available." although   libxcomposite1 and libxdamage1 are installed.

some days ago i installed the new official ati drivers for my radeon xpress 200, so that i can use it with aixgl but i did not do anything more than that because i do not know if i have to another xserver like it was necessary for xgl

anyone knows what to do?

thanks basdi

---

### Post by A3aan on 2008-01-14
I have the same problem too, but I am using Kubuntu (I hope I'm still allowed to post this here, since this is an Ubuntu forum..?).

I upgraded from Feisty Fawn to Gutsy Gibbon, to have a more recent version of Ubuntu before installing KDE4.
Once KDE4 was installed on Gutsy Gibbon, the composit features worked, but the screen resolution was very strange (both low and with a strange ratio). 
I noticed that it was possible to get new proprietary drivers for my Ati 9600 Radeon graphics card, so I installed those.
After that, the tab 'Desktop Effects' says "Compositing is not supported on your system. Required X extensions (XComposite and XDamage) are not available.".

I guess this is a new bug and hope that more people become aware of it, so that it will be fixed :)
Has anyone got suggestions on who to contact about this bug and how to contact those people?

Thanks in advance!

Greetings,

Adriaan

(btw, should we make a bug report about this? Or has that already been done?)

---

### Post by ChainedGhost on 2008-01-14
> **A3aan said:**
> I have the same problem too, but I am using Kubuntu (I hope I'm still allowed to post this here, since this is an Ubuntu forum..?).

I upgraded from Feisty Fawn to Gutsy Gibbon, to have a more recent version of Ubuntu before installing KDE4.
Once KDE4 was installed on Gutsy Gibbon, the composit features worked, but the screen resolution was very strange (both low and with a strange ratio). 
I noticed that it was possible to get new proprietary drivers for my Ati 9600 Radeon graphics card, so I installed those.
After that, the tab 'Desktop Effects' says "Compositing is not supported on your system. Required X extensions (XComposite and XDamage) are not available.".

I guess this is a new bug and hope that more people become aware of it, so that it will be fixed :)
Has anyone got suggestions on who to contact about this bug and how to contact those people?

Thanks in advance!

Greetings,

Adriaan

(btw, should we make a bug report about this? Or has that already been done?)

Same here. (including 9600) I'll try installing the latest ati driver instead of the one from the repository and see what happens. I think either it needs AIGLX/XGL or it has something to do with my xorg.conf

---

### Post by ChainedGhost on 2008-01-14
I was right it looks like XGL/AIGLX is required [look here]("http://websvn.kde.org/trunk/KDE/kdebase/workspace/kwin/COMPOSITE_HOWTO?revision=749632&view=markup")

---

### Post by A3aan on 2008-01-17
Indeed, have you tried to install XGL/AIGLX drivers yet?
I will try to in the near future, but I don't have much time the next two weeks..
Greetings Adriaan

---

### Post by onlineapps on 2008-01-17
xserver-xgl let me be able to enable it, but none of the effects actually turned on....

---

### Post by insertAlias on 2008-01-17
> but none of the effects actually turned on....

I'm at this point.  Compiz works for me in gnome, but when I enable desktop effects, nothing happens.

---

### Post by A3aan on 2008-03-05
Has anyone been able to fix this problem yet?

I would really like to know!

Greetings,

Adriaan

---

### Post by keforex on 2008-05-10
+1 here with the same problem. How can I report this as a bug? I did several searched here but nothing seems to work. HELP!!!

---

### Post by inportb on 2008-05-10
This is on Gutsy, right? It might be necessary to edit the xorg.conf to add the composite and damage extensions.

---

### Post by keforex on 2008-05-10
I already have those tags in the xorg.conf and it still doesn't work.

---

### Post by dvstin on 2008-05-18
desktop effects worked out of the box with kde4 remix kubuntu 8.04 cd on my thinkpad x300 (intel graphics)

---

