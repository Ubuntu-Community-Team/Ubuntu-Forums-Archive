---
title: "Request: Inkscape .42"
date: 2005-07-27
forum: Deferred/Invalid Requests
---

### Post by benplaut on 2005-07-27
Just Released!

[www.inkscape.org](www.inkscape.org)

i beleive they have a .DEB, but i haven't gotten a chance to test it

---

### Post by vvlist on 2005-07-27
I want it too!   :smile:

---

### Post by charlieg on 2005-07-27
The impatient could always try the autopackage version available from the download page. ;)

---

### Post by graigsmith on 2005-07-27
OMG autopackage is freaking easy.  just enable the run permission and run it.  and it even asks you for your password when it needs it and installs it perfectly.  it even downloaded some stuff that it needed to install it   :)

OMG YAY the gradient filling is insanely easy with this version. :)

---

### Post by vvlist on 2005-07-27
just get the autopackage, it IS easy!

---

### Post by keifer on 2005-07-27
[QUOTE=vvlist]just get the autopackage, it IS easy![/QUOTE]
 sadly, they don't have a ppc autopackage. :(

---

### Post by graigsmith on 2005-07-28
[QUOTE=keifer]sadly, they don't have a ppc autopackage. :([/QUOTE]
 does the autopackage fail or the ppc system? shouldn't it download what it needs if its missing?

---

### Post by abandoned_hussam on 2005-07-28
[QUOTE=benplaut]Just Released!

[www.inkscape.org](www.inkscape.org)

i beleive they have a .DEB, but i haven't gotten a chance to test it[/QUOTE]
 do you have a link to their .deb?

---

### Post by codejunkie on 2005-07-28
[QUOTE=hussam]do you have a link to their .deb?[/QUOTE]
it's on inkscape's page at sourceforge but it doesn't work with ubuntu i tried last night but the autopackage works pretty good.

---

### Post by tristan on 2005-07-28
Just alien the static rpm, it works like a charm! 

0.42 is pretty sweet...

---

### Post by Virtual DarKness on 2005-07-28
I've installed it with the autopackage (great tool!) and seems to work fine; 

just one thing.. if you draw a shape, let's say a rectangle and you go on the Fill and Stroke dialog, under the stroke style tab you shouldn't see the content of the dashes combo box..

and also it outputs this warning in terminal:
> (inkscape:10277): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24


Am I the only one who have this problem? Or is just a problem that happens with autopackage+ubuntu? .. 

bye,
Giovanni.

---

### Post by jdong on 2005-07-28
I've already dealt with this a few days back; it doesn't build on Hoary, due to new libraries.

---

### Post by charlieg on 2005-07-28
[QUOTE=Virtual DarKness]Am I the only one who have this problem? Or is just a problem that happens with autopackage+ubuntu? .. [/QUOTE]
Change your colordepth in X to 32 or somehow configure Inkscape to use a lower colordepth.  If you don't wish to do the former and can't do the latter, let the Inkscape team know as I'm sure it's something they'll either address or give you a comforting "don't worry" reply.

---

### Post by SickTwist on 2005-07-30
Inkscape 0.42.1 is supposed to be released soon to correct some breakage in 0.42.  Perhaps backporting should wait a few days until the patch is released.

---

