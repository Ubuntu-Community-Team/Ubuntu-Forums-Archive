---
title: "Gimp 2.8"
date: 2012-06-03
forum: Desktop Environments
---

### Post by redman5087 on 2012-06-03
Gimp 2.8 is unusable in Single Window Mode.

The first time a start gimp 2.8 you have the "minimum,maximum,close" button in the corner.

The second time you start gimp 2.8 the "maximize" button is gone and there is no possibility to adjust the window to fit the screen.

Please help

Kind regards,

Patrick

---

### Post by traditionalist on 2012-06-03
> **redman5087 said:**
> Gimp 2.8 is unusable in Single Window Mode.

The first time a start gimp 2.8 you have the "minimum,maximum,close" button in the corner.

The second time you start gimp 2.8 the "maximize" button is gone and there is no possibility to adjust the window to fit the screen.

Please help

Kind regards,

Patrick

Hmmm....there must be something wrong with your setup, It works perfectly for me in single window mode or otherwise. Perhaps try a reinstall?

[[IMG]http://img641.imageshack.us/img641/1977/bow16imported30rgbcolor.th.png[/IMG]](http://img641.imageshack.us/i/bow16imported30rgbcolor.png/)

---

### Post by redman5087 on 2012-06-04
I did some further investigation.

Ubuntu 12.04 Unity, everything works
Ubuntu 12.04 Gnome Shell, everything works
Ubuntu 12.04 Gnome Classic, maximize button is gone

I think it is a bug

---

### Post by traditionalist on 2012-06-04
> **redman5087 said:**
> I did some further investigation.

Ubuntu 12.04 Unity, everything works
Ubuntu 12.04 Gnome Shell, everything works
Ubuntu 12.04 Gnome Classic, maximize button is gone

I think it is a bug

Have you tweaked anything else?  There are a few ways the maximise button could disappear.

---

### Post by redman5087 on 2012-06-04
I changed the metacity button layout from left to the right.

I changed it back like it was and this doesn't help.

For the rest I tweaked nothing.

---

### Post by redman5087 on 2012-06-04
Got it.

I changed <ithin Gimp with preferences the theme from default to small

---

### Post by traditionalist on 2012-06-04
> **redman5087 said:**
> Got it.

I changed <ithin Gimp with preferences the theme from default to small

Good that you got it working, but it should work with all themes. There must be a tweak on it somewhere. This doesn't matter much if you are the only user and you only have a couple of tweaks, but over time, updates etc, these things accumulate and eventually make stuff unusable.

---

### Post by jceresini on 2012-10-23
I had the same issue in Fedora. Changing the theme to small fixed it. Changing it immediately back to the default also worked and showed me the maximize button. I think its a bug in Gimp

---

