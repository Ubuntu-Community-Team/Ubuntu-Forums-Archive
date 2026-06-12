---
title: "[SOLVED] No Cube Effect after Ubuntu Studio Install"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by iheartubuntu on 2007-09-30
I installed Ubuntu Studio... very nice. But now I have no cube effect. Anyone know how to get it back? Terminal code? Nothing in the archives are very helpful. Thanks!

---

### Post by Forlong on 2007-09-30
> **shirteesdotnet said:**
> I installed Ubuntu Studio... very nice. But now I have no cube effect. Anyone know how to get it back?
```
sudo apt-get install desktop-effects
```

---

### Post by iheartubuntu on 2007-09-30
Thanks so much for the help. I did insert this into terminal and It did not revert back to the cube.

I got the following message:

"desktop-effects is already the newest version."

---

### Post by Forlong on 2007-09-30
Ah, OK.... I thought you did a clean install of Ubuntu Studio, where desktop-effects isn't installed by default.

So what exactly is your problem?
It seems like it did work for you, so please elaborate on what you did.

---

### Post by iheartubuntu on 2007-09-30
I installed Ubuntu, then installed the Studio package and lost the cube effect I had in the regular Ubuntu. I pretty much like the Ubuntu Studio, but would like the cube effect back. 

Any tips? Much appreciated!

---

### Post by Forlong on 2007-10-01
Run ```
gconf-editor
``` and make sure

**/apps/compiz/general/screen0/options/hsize** is set to **4**
**/apps/compiz/general/screen0/options/number_of_desktops** is set to **1**
**/apps/compiz/general/screen0/options/vsize** is set to **1**

---

