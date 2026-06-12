---
title: "[SOLVED] Transparent window borders"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by theelk801 on 2007-10-31
I don't know how to make my window borders semi-transparent. I tried to change them in the theme preferences, but no luck. Any help would be much appreciated. I am running Gutsy with the Compiz Fusion control panel installed.

---

### Post by brunovalentino on 2007-10-31
Try this.
Install the Emerald Theme Manager.
And then you can customize your window borders from there.

Worked for me, hope it does for u.

---

### Post by theelk801 on 2007-11-01
Uh, how exactly do I install? I haven't been able to install stuff. Isn't there an apt-get or something?

---

### Post by chrisccoulson on 2007-11-01
You can get transparent Metacity themes whilst running Compiz, by modifying the following gconf keys:

/apps/gwd/metacity_theme_active_opacity

and

/apps/gwd/metacity_theme_opacity

You can modify these via gconf-editor.

---

### Post by theelk801 on 2007-11-01
And what does that mean?

---

### Post by chrisccoulson on 2007-11-01
Open a terminal (Applications -> Accessories -> Terminal)

Type:
```
gconf-editor
```

Navigate to /apps/gwd using the left-hand pane. The keys I mentioned will appear in the right hand pane. Set them to values between 0 (fully transparent) and 100 (fully opaque) by double-clicking on them. 'metacity_theme_active_opacity' will define the transparency of your window borders for active windows. 'metacity_theme_opacity' will define the transparency for inactive windows.

---

### Post by theelk801 on 2007-11-01
Thank you so very, very much. I appreciate the help.

---

