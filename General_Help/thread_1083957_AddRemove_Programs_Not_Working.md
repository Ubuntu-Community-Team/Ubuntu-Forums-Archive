---
title: "Add/Remove Programs Not Working"
date: 2009-03-01
forum: General Help
---

### Post by codeking on 2009-03-01
When I open up add/remove programs everything goes as normal but theres absolutely no items in the software list and no items in the category list as well.  What could be causing this?

---

### Post by oldos2er on 2009-03-01
Do you have it set to show all available apps? If so, run
```
sudo apt-get update
```
in a terminal, then try it again.

---

### Post by codeking on 2009-03-03
Nope, still nothing

---

### Post by bodhi.zazen on 2009-03-03
OUCH, I have no idea. My only suggestion is more a work around, try synaptic.

---

### Post by mb_webguy on 2009-03-04
Try "sudo update-apt-xapian-index".

---

### Post by codeking on 2009-03-05
Still nothing.  This is really odd :???:

---

### Post by plucky on 2009-03-05
Try a re-install ```
sudo apt-get install --reinstall gnome-app-install
```


Good Luck

---

### Post by codeking on 2009-03-07
Thank you plucky!  That worked!

Wonder why it broke in the first place :S

---

