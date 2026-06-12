---
title: "Loading Background and Idesk when Fluxbox Starts."
date: 2005-07-06
forum: Desktop Environments
---

### Post by docmur on 2005-07-06
Hello I need some help figuring out how to make my background and my idesk conf load when fluxbox starts thanks!

---

### Post by bdamon on 2005-07-06
[QUOTE=docmur]Hello I need some help figuring out how to make my background and my idesk conf load when fluxbox starts thanks![/QUOTE]


As I remember one option would be to use a .xsession file if you use a graphical login manager or  a .xinitrc file if you use startx. Create the file in your home directory. You can run idesk and what ever program you use to set the background out of these files.
Something similar to

idesk &
background program &
exec fluxbox 


Ben

---

