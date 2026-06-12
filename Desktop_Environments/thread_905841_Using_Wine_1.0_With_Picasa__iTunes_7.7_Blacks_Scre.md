---
title: "Using Wine 1.0 With Picasa / iTunes 7.7 Blacks Screen"
date: 2008-08-30
forum: Desktop Environments
---

### Post by nuclear88 on 2008-08-30
I successfully installed iTunes 7.7 and Picasa2 on a fresh install of Ubuntu 8.04 with Wine 1.0. Both programs seem to work fine, however whenever I start one of them, the screen blacks for a moment, then comes back when the picasa or itunes window shows up, but the toolbars still stay black until you do something to change them. It seems like they just aren't getting redrawn or something. Is anyone having a problem similar to this?

Also, I switched back to metacity to make sure it wasn't compiz's fault.

Thanks for your help!

---

### Post by AliTabuger7 on 2008-08-30
I used to have the exact same thing happen. I think it has to do with my Nvidia special drivers.

Workaround is to configure wine to do all of wine applications inside of a virtual desktop.

---

### Post by EnGorDiaz on 2008-08-30
> **AliTabuger7 said:**
> I used to have the exact same thing happen. I think it has to do with my Nvidia special drivers.

Workaround is to configure wine to do all of wine applications inside of a virtual desktop.

not true i had it on my extreme graphics its a fault with all graphics cards its because the windows XUL runner application doesnt work you need to patch it with a program forgotten the name but its quite dangerous running itunes as it can flicker your x server like that i tryed to get itunes working once nearly broke my x server you need to patch it

---

### Post by EnGorDiaz on 2008-08-30
bcus some direct x apps dont work with the x server bcus wine emulates your drivers causing them to clash its the same with cross office thats why i never buy cross office most windows programs dont even work on cross office but its non free

---

