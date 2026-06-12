---
title: "change volume/brightness adjustment intervals"
date: 2009-06-07
forum: General Help
---

### Post by JamesSmith on 2009-06-07
Hi there,

I was wondering, is it possible to alter the step interval of the volume and screen brightness on-screen graphics in Jaunty? Reason being is that when I press Fn+LEFT/RIGHT or Fn+UP/DOWN, the netbook reaches the limits of adjustment long before the graphic has.

I could probably go from min to max brightness/volume 3 or 4 times over before the graphic shows full brightness/volume and I though it would be nice to modify that so that it is more representative.

I hope that makes sense to someone!  Would love to hear your thoughts...
Cheers, James

P.s.  Acer Aspire One A150-Ab with Ubuntu 9.04 NBR  :D

---

### Post by sigixv on 2009-06-07
you can use the sliders with your mouse

Volume control is in a standard config located at your top-right;
brightness setting can be found by right clicking a panel and adding it, the symbol is a white circle with small bars sticking out (somewhat looking like a sun). I think the name in english will be something like "brightnessapplet" (i'm running dutch version, so i'm not sure)

---

### Post by sdennie on 2009-06-07
I'm not sure about screen brightness but you can change the volume control step by hitting Alt-F2 and typing gconf-editor.  Then navigate to /apps/gnome-settings-deamon and change the volume_step to something different.

---

