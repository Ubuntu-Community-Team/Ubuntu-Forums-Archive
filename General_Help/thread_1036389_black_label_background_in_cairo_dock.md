---
title: "black label background in cairo dock"
date: 2009-01-10
forum: General Help
---

### Post by BigT0 on 2009-01-10
hey...

im with ubuntu hardy...
a few weeks ago i installed cairo dock (1.6.3.2) successfully, all worked fine. after changing system fonts, i started to see a black background behind icon labels. i changed back to default fonts and it didnt help. i got compiz working and i upgraded to cairo dock 2.0 and still the ugly black background!!

i attached a screenshot.....

---

### Post by fabounet on 2009-01-10
did you set a background for labels ? if not, you can try to do that

---

### Post by xrdguy on 2009-01-11
you have to enable visual effects.. so go to system>preferences and then apperance then visual effect. make sure it is not checked on none at least enable normal visual effects.

---

### Post by BigT0 on 2009-01-11
well fabounet,
no background set for labels and even when set, still, i get the black background.

xrdguy, i got "extra" visual effects already running...

---

### Post by BigT0 on 2009-01-15
well...  i found out that it has something to do with libcairo and compiz
but i dont seem to find the solution...
this thing is really ugly and annoying...

---

### Post by fabounet on 2009-01-15
did you try Cairo-Dock 2 ? (if you have an NVidia or an Intel with the last xserver)

---

### Post by BigT0 on 2009-01-17
i installed cairo-dock 2 but sill no improvment..
i have an intel intergrated graghics card. how do i update to last xserver?

---

### Post by CitizenX on 2009-01-23
for myself, the black background will appear if I dont have compositing turned on. Double check that you've got Effects turned on...alternatively you can make metacity a compositing manager.

run gconf-editor (or Configuration Editor in System Tools if you have it there)

apps > metacity > general > compositing_manager (check it)

---

### Post by BigT0 on 2009-01-25
Well, I googled around a bit more and I found that for some reason libgl1-mesa-dri uninstalled itself or something so I ```
sudo apt-get install libgl1-mesa-dri
```
reboot

and it works beautiful without any ugly black background behind the icon labels.
It was all about the rendering!!!

Thanks for all who helped!!!

(marking as solved)

---

