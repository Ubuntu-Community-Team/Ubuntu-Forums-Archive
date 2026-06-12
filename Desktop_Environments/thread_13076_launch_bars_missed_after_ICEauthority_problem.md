---
title: "launch bars missed after ICEauthority problem"
date: 2005-01-28
forum: Desktop Environments
---

### Post by T31 on 2005-01-28
like the title of the post says, i have no launch bars, this evening watching a film in totem i had a problem wih the sound so i reboot the desktop, the next surprise was that the sessions did last less than 10 seconds saying problem with the ICEauthority file, i did:

sudo chown user:user .ICEauthority and i could start the gnome desktop but now i have no launch bars at all, ](*,) 

please someone can help me to get them back?

Thanks in advance :)

---

### Post by Rancoras on 2005-01-28
Does right clicking on the desktop bring up the menu?  If so you should be able to add the panels back.

---

### Post by T31 on 2005-01-28
thats not working :(  :cry:

---

### Post by Rancoras on 2005-01-28
Try dropping to command line with and ALT+F1 then issuing:
```
sudo apt-get install --reinstall gnome-panel
``` 
Then reboot.

That has worked for me in the past.

---

### Post by T31 on 2005-01-30
hey thx!  :D in fact i already did but only typing 

sudo apt-get install gnome-panel  :mrgreen: 

Anyway thx a lot :D

---

