---
title: "Replace logo"
date: 2006-09-07
forum: Desktop Environments
---

### Post by statue on 2006-09-07
Is there a way to replace the ubuntu logo next to "Applications" on the menubar? Id like something to go with my theme better, it seems like it would be easy enough but I cant find a tutorial, thanks.

---

### Post by ayoli on 2006-09-07
replace icon named distributor-logo.png in your icon theme or in inherited icon theme.

---

### Post by statue on 2006-09-07
Thanks for the suggestion but it seems that distributor-logo.png in usr/share/icons/48x48/apps is used only under the "System" panel for "About Ubuntu." I want to change the main menu icon, any ideas what this file is called?

---

### Post by ayoli on 2006-09-07
gnome-main-menu.png

---

### Post by statue on 2006-09-07
I dont believe that to be the image as it is the gnome foot, I am guessing it is the image used under "System" for the "About GNOME" link.

---

### Post by ayoli on 2006-09-07
> **statue said:**
> I dont believe that to be the image as it is the gnome foot, I am guessing it is the image used under "System" for the "About GNOME" link.
the icon name for main menu is gnome-main-menu.png, 
btw, try in a term:
```
locate gnome-main-menu.png
```
and:
```
locate distributor-logo.png
```
have a look to all of them.

---

### Post by crossedout on 2006-09-07
ayoli is correct, the name of the icon is distributor-logo.png (assuming of course we interpret your question correctly).  Make sure you are placing the icon in the proper theme location.

-Xout

---

### Post by statue on 2006-09-12
I stand corrected. You were right about the distributor-logo.png. Turns out after I installed a new program then it suddenly changed. Not sure why it diddnt appear when I first refreshed gnome though. Little odd but hey it works now so who cares. Thanks for the help.

---

