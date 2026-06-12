---
title: "Migrating touchpad settings into xfconf ignores &quot;Synaptics Move Speed&quot;?"
date: 2021-01-03
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2021-01-03
I have for a long time used custom configuration method for my touchpad: [FONT=Courier New]synclient -l[/FONT] output is stored in a file, and a script is run on login to restore it back through [FONT=Courier New]synclient[/FONT].  I would like to move these settings into xfconf as described [here]("https://docs.xfce.org/xfce/xfce4-settings/mouse#device_properties").

I wrote a script to convert the [FONT=Courier New]xinput list-props[/FONT] output into xfconf, that part works fine.

But unplugging & plugging in my touchpad does not correctly apply "Synaptics Move Speed"?

Comparing [FONT=Courier New]xinput list-props[/FONT] output for my touchpad:

[LIST]
[*]Default of this setting, without any config -
```
Synaptics Move Speed (576):	1.000000, 1.750000, 0.112296, 0.000000
```

[*]Desired -
```
Synaptics Move Speed (576):	2.000000, 9.000000, 0.000000, 0.000000
```

[*]What xfce sets -
```
Synaptics Move Speed (576):	2.000000, 0.000000, 0.112296, 0.000000
```
[/LIST]
:confused:

All other settings seem applied correctly.  Settings Editor shows the correct value for "Synaptics_Move_Speed".

How to get Xfce to apply "Synaptics Move Speed" correctly?

---

### Post by &amp;KyT$0P# on 2021-01-10
bump

---

### Post by &amp;KyT$0P# on 2021-01-17
bump

---

### Post by &amp;KyT$0P# on 2021-01-25
bump

---

### Post by &amp;KyT$0P# on 2021-02-03
bump

---

### Post by &amp;KyT$0P# on 2021-02-17
bump

---

### Post by #&amp;thj^% on 2021-02-17
h2 have a look see, maybe? [https://gist.github.com/ivan/c35e798d4f32e37c1714ec5beec30d16](https://gist.github.com/ivan/c35e798d4f32e37c1714ec5beec30d16)

---

### Post by &amp;KyT$0P# on 2021-02-19
Sorry 1fallen I don't understand what you're suggesting?  Are you suggesting I try to put this property in a xorg.conf.d file instead of trying to set it through Xfce?

---

### Post by #&amp;thj^% on 2021-02-24
Both, it's a bit trial and error though I'm afraid.

---

### Post by &amp;KyT$0P# on 2021-03-22
Sorry for the unexpected delay in being able to get back to this.  Something else fishy is going on with that property - though applying it in a xorg.conf.d file did apply it, that made my touchpad WAY too fast.  Anyway I think with this I should be able to achieve what I want, just will take some fiddling to get it right for me, so considering this solved.  Thanks 1fallen! :KS

* After some more playing with this property, I conclude I actually don't want to explicitly set it at all.  I got the desired effect by leaving "Synaptics Move Speed" alone, instead going to Xfce Mouse & Touchpad settings and set Acceleration to 0 and Sensitivity to 1px.  Can't believe I didn't think of trying those settings sooner #-o

---

