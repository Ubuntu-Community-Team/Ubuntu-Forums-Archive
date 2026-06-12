---
title: "Gnome freeze"
date: 2007-10-26
forum: Desktop Environments
---

### Post by joeri_83 on 2007-10-26
Every now and then (way too often) everything seem to freeze, and the screen will only get repainted while I move the mouse. As far as I can tell it can only be sortet out by restarting (ctrl-alt-backspace), which is very annoying. It doesn't seem to matter whether I use Compiz or not, and I currently have it turned off. My graphics card is a Geforce 6600 GT, using the restricted NVidia drivers.

Anyone else having this problem? Any ideas of how to fix it?

---

### Post by joeri_83 on 2007-10-26
To be more specific it seems to freeze when it has to load new things, such as a website or an application. It repaints the screen fine with things already loaded though.

---

### Post by hamvil on 2007-10-26
Same thing is happening to me. This new release of ubuntu is far less responsive than the previous. 

PS I'm not running compiz.

---

### Post by tajensen72 on 2007-10-29
I think this is the same problem I'm having.  If I switch out of X to a terminal (<ctrl><alt>F1) and then back (<alt>F7), it then unfreezes.  Do you see the same thing?

tj

---

### Post by Jhongy on 2007-10-29
Most likely the nVidia drivers -- I found the latest version to be extremely buggy on older GeForce cards. In the end (after trying and failing to change drivers manually), I downloaded Envy and switched to the earliest nVidia driver it offered -- solved lots of screen redraw (and lockup) problems.

---

