---
title: "GUI of gedit in Kubuntu is weird"
date: 2011-11-18
forum: Desktop Environments
---

### Post by tutelary oatmeal on 2011-11-18
Hello,

I recently installed Kubuntu 11.10 on a laptop and there is something odd about the graphics. The GUI looks simple and several years old for some reason. This is also affecting document viewer in Kubuntu 11.10. It seems like Gnome programs are not being displayed properly and I did not have this problem in Kubuntu 11.04.

I have attached a picture of gedit and it is from from my laptop. I have since tried to fix it by using suggestions from other users (I do not remember all details, but it involves either installing another package or editing some text file of user settings) but to no avail. I recently installed Kubuntu 11.10 on a desktop and the problem is the same after installing gedit on a freshly installed Kubuntu.

Another strange thing with gedit in Kubuntu 11.10 is that whenever I open up a document from Dolphin for editing in gedit, gedit also opens an empty document named "Untitled Document x" where x is a number.

Does anybody have any suggestion for how to fix this?

---

### Post by dniMretsaM on 2011-11-18
Make sure the compositing type is set to OpenGL (System Setting -> Desktop Effects -> Advanced -> Compositing type). This will give you a better looking desktop than XRender (but it might be incompatible with older hardware). Also change the theme/window decoration/color scheme around. You could also fiddle around with the settings in System Setting -> Application Appearance -> GTK+ Appearance.

---

### Post by tutelary oatmeal on 2011-11-18
> **dniMretsaM said:**
> Make sure the compositing type is set to OpenGL (System Setting -> Desktop Effects -> Advanced -> Compositing type). This will give you a better looking desktop than XRender (but it might be incompatible with older hardware).

I managed changing to OpenGL. The computer gives me a warning at first (don't remember the exact wording) and the switch fails on this attempt (it switches back to XRender). On the second attempt, there is no warning and the switch goes fine. OpenGL is selected in System Settings, so I reckon that this implies success for the switch to OpenGL.

The GUI of gedit remains the same though.

> **dniMretsaM said:**
> Also change the theme/window decoration/color scheme around. You could also fiddle around with the settings in System Setting -> Application Appearance -> GTK+ Appearance.

For example, switching the widget style between Raleigh and oxygen-gtk makes no difference.

---

### Post by tutelary oatmeal on 2011-11-18
Check if the icon in the task manager gives you any clue. It is gedit. I think that that 'X' did not appear in Kubuntu 11.04 for gedit (unsure though).

---

### Post by Copper Bezel on 2011-11-18
Guys, is this related to the fact that the apps tutelary is referring to are written in GTK3?

> Another strange thing with gedit in Kubuntu 11.10 is that whenever I open up a document from Dolphin for editing in gedit, gedit also opens an empty document named "Untitled Document x" where x is a number.
I get the same (two tabs) under Shell if I run gedit with --new-window, but not when I open an associated file from Nautilus or the Dash.

---

### Post by tartalo on 2011-11-18
> **Copper Bezel said:**
> Guys, is this related to the fact that the apps tutelary is referring to are written in GTK3?

Yes, there's an Oxygen theme for GTK3 apps but it's unfinished. Anyway:
[http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

---

### Post by dniMretsaM on 2011-11-18
> **Copper Bezel said:**
> Guys, is this related to the fact that the apps tutelary is referring to are written in GTK3?

I don't think so. GIMP is written in GTK3 (I think) and that doesn't seem to have any problems.

---

### Post by Copper Bezel on 2011-11-18
GIMP 2.6 (stable) is still GTK2. gedit and Evince are both GTK3.

---

### Post by dniMretsaM on 2011-11-18
I use GIMP 2.7.x and when I run
```
sudo apt-get remove libgtk-3-0
```
It removes GIMP too.

---

### Post by Copper Bezel on 2011-11-18
Wait, back up then. Are you saying that you see the same problem tutelary does with gedit?

---

### Post by tutelary oatmeal on 2011-11-19
> **Copper Bezel said:**
> Wait, back up then. Are you saying that you see the same problem tutelary does with gedit?

The GUI of GIMP looks OK for me. The graphics does not look ancient like in the case of gedit.

---

### Post by dniMretsaM on 2011-11-19
> **Copper Bezel said:**
> Wait, back up then. Are you saying that you see the same problem tutelary does with gedit?

No, I'm saying that I don't have the same problem. That's why I was wondering whether or not it's a problem with GTK3 apps.

> **tutelary oatmeal said:**
> The GUI of GIMP looks OK for me. The  graphics does not look ancient like in the case of gedit.

Which version of GIMP are you using? 2.6.x or 2.7.x?

---

### Post by tutelary oatmeal on 2011-11-19
> **dnimretsam said:**
>  which version of gimp are you using? 2.6.x or 2.7.x?

2.6.11

---

### Post by tutelary oatmeal on 2011-11-19
Does this give you any clue? If loading gedit from the command line, I get this error message:

```
dagge@dagge-dator:~$ gedit

** (gedit:30457): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme
```

---

