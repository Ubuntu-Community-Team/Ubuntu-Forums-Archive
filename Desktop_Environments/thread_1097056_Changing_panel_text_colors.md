---
title: "Changing panel text colors"
date: 2009-03-15
forum: Desktop Environments
---

### Post by alanfang on 2009-03-15
Is there a way to change the color of the text on just panels? Also, is there a way to customise what the panels look like when you hover over them etc? Thanks for the help.

---

### Post by m_duck on 2009-03-15
The former can be done using "gnome-color-chooser" - I believe that's what the package is called and it lets you choose the colours/fonts etc of various parts of gnome individually.

As for the latter, I think that's written in with the theme so check out gnome look for a whole load.

---

### Post by alanfang on 2009-03-15
Thanks, does anyone know of a pre compiled package for gnome color chooser? I can't seem to get it to install from source.

---

### Post by s.fox on 2009-03-15
Hi,

I started a thread on the same topic about 5misn ago. :D [LINK]("http://ubuntuforums.org/showthread.php?t=1097299")

I have been able to set the font colour  of the panel.  AS for the colour choser try gcolour2.

```
sudo apt-get install gcolor2
```

then

```
gcolor2
```

hope this helps.

-Ash R

---

### Post by m_duck on 2009-03-16
As far as I know, gcolor2 is just a program to find what colours are by clicking on them?

Have you tried installing gnome-color-chooser from the repo's? Either open Synaptic (System -> Administration -> Synaptic Package Manager) and search for it or from the terminal (Applications -> Accessories -> Terminal)```
sudo apt-get install gnome-color-chooser
```The former method is probably better just in case I have got the name wrong.

---

### Post by alanfang on 2009-03-16
Okay I got gnome color chooser installed. It worked great for changing the text colors. Is there a way to change the background color of a selected item in the panel? Right now it seems to be stuck on the ubuntu default.

---

### Post by m_duck on 2009-03-16
As far as I'm aware I think that the theme in use determines the backgrounds of selected items etc. If that isn't the case, I'm not sure how to change it - perhaps a line in your ~/.gtkrc-2.0 - but really, I've no idea. Hope I've been of some use.

---

