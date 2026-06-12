---
title: "Can't get desktop cube in compiz to work in 7.10"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by CanadianNorth on 2007-10-24
hey there,

I installed compiz on a pair of dells (640M and 3100). These are both running 7.10.

I can get some effects to work, but can't get the desktop cube to work.

Right now, I can't change desktops on either machine at all......


help!  -- I suspect there is something very simple I am missing.


:confused:

---

### Post by alwiap on 2007-10-24
what guide did you use to install compiz?

I would suggest setting up compiz with this guide: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

as far as the desktop cube, did you make sure to "increase the number of the virtual desktops to 4 at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size"?

---

### Post by Inxsible on 2007-10-24
Have you installed CCSM in 7.10?

It doesn't come installed by default. Strange, I know !!

Install it by ```
 sudo aptitude install compizconfig-settings-manager
```Then do what alwiap said under General Options --> Desktop Size and increase the Horizontal Virtual Size to 4. Also make sure the Desktop Cube and Rotate Cube plugins are turned on.

---

### Post by ItsMitsHere on 2007-10-24
go to compiz config settings manager and click general options (top most option), in the next window click third tab called desktop size. there on the right side place values 4, 1 and 1 on the three boxes top to bottom. now go back to main window and make sure that under the desktop effects lable the desktop cube and rotate cube are enabled and all other are disabled. if it works for you u can then try out some more effects. to rotate the cube you should hold alt+ctrl and press left-right keys.
__________________

---

### Post by rundee_f on 2007-10-24
if your problem still persists, i suggest u to reinstalling compizfusion... u might find [http://forlong.blogage.de/#blogentry_451](http://forlong.blogage.de/#blogentry_451) very usefull... (it did to me though)

---

### Post by CanadianNorth on 2007-10-24
Thanks,

I used the guide, [http://forlong.blogage.de/article/20...-Compiz-Fusion](http://forlong.blogage.de/article/20...-Compiz-Fusion), which worked.

seems I missed a checkmark somewhere.

---

