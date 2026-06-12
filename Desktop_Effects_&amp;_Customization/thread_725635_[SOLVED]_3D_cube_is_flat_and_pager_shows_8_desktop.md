---
title: "[SOLVED] 3D cube is flat and pager shows 8 desktops"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by uberlube on 2008-03-15
I changed my horizontal desktop size to 4 and now I have my cube. The only problem is that now my pager shows that I have 16 desktops. :confused:

---

### Post by Diabolis on 2008-03-15
Check your compiz settings. Type in terminal the following:

```
gconf-editor
```

and then

```
apps/compiz/screen0/options
```

look for hsize and number_of_desktops

---

### Post by uberlube on 2008-03-15
there is no compiz under apps

---

### Post by Diabolis on 2008-03-15
Strange, I don't know why compiz is not showing up inside Configuration editor, It should.

---

### Post by uberlube on 2008-03-15
I am using KDE right now, not gnome. That may be the issue. Any ideas about how to do this from KDE?

---

### Post by Diabolis on 2008-03-15
I use mostly gnome, so I'm not sure. Try looking for something similar in "kcontrol"

---

### Post by hyperair on 2008-03-16
Open CompizConfig Settings Manager, or "Advanced Desktop Effects Settings". Under General->Desktop Size, edit the number of desktops to 0.

---

### Post by uberlube on 2008-03-16
I tried to set it to 0 but it makes you have at least 1. After that I enabled desktop effects again and still have the same problem.

---

### Post by durand on 2008-03-16
Right click on the pager in the gnome-panel and change the setting to 4 or whatever.

---

### Post by uberlube on 2008-03-16
Didn't work. I would also like to say the of the 16 desktops that the pager shows, only the first 8 are useable.

---

### Post by durand on 2008-03-16
what about the other settings in desktop size?

---

### Post by uberlube on 2008-03-16
Horizontal = 4
Vertical = 1
Number of desktops = 4

---

### Post by durand on 2008-03-16
Ah, there you go! Its 4-1-1 on mine. The desktop setting there are the virtual desktops per cube face, or whatever. Change the 4 to 1.

---

### Post by uberlube on 2008-03-16
Thanks dude, I tried doing that before but it didn't take for some reason, it would always rever back to 4. This time i just clicked on restore default and it stayed at 1.

---

### Post by durand on 2008-03-16
yay :D

---

### Post by uberlube on 2008-03-16
Also 1 more question. For some reason i cannot drag an open windows from one desktop to another. How can i activate this?

---

### Post by durand on 2008-03-16
Activate the rotate cube plugin, then tick the edge flip options..not sure which one exactly.

---

### Post by hyperair on 2008-03-16
Edge flip move or something if I'm not mistaken

---

### Post by uberlube on 2008-03-16
U the man! :)

---

### Post by Patto77 on 2008-03-20
This is exactly what I was looking for!  I had gnome sorted, but just couldn't get KDE to do the same.

---

