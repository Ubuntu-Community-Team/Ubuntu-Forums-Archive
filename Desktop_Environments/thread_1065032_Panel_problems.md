---
title: "Panel problems"
date: 2009-02-09
forum: Desktop Environments
---

### Post by pvravi on 2009-02-09
Hi, 

I am not sure what exactly caused this, but if I start a gnome-panel as myself: 

$ gnome-panel

It starts a blank panel. However, if I start one as root: 

$ sudo gnome-panel

The correct panel with the right applets starts up.

It would appear that the root account has the correct configs for the panel, while my user does not. How do I fix this? Should I import the panel configs form the root account into mine? How do I do this? Which exact files? 

I'm running gnome - in particular HP's MIE interface.

Thanks
pvravi

---

### Post by gettinoriginal on 2009-02-09
It is such a minor thing to add the applets, just create a blank and set it how you want.  :P

---

### Post by pvravi on 2009-02-09
> **gettinoriginal said:**
> It is such a minor thing to add the applets, just create a blank and set it how you want.  :P

gettinoriginal, not so on the HP MIE interface :(. The only options available on Right-click on the panel are Help and About. No "add to panel" or any of the others.

---

### Post by blackened on 2009-02-09
You sure your theme's not using a broken panel.rc? Try changing themes and see what happens. Note: this won't work if your root themes are symlinked to your user themes.

---

### Post by pvravi on 2009-02-09
> **blackened said:**
> You sure your theme's not using a broken panel.rc? Try changing themes and see what happens. Note: this won't work if your root themes are symlinked to your user themes.

Unable to change theme in the real sense now - If I change themes, only the window borders, etc change. The frontend remains that of the HP MIE interface. Perhaps the only way to get back is to uninstall the HP interface debs I installed.

---

