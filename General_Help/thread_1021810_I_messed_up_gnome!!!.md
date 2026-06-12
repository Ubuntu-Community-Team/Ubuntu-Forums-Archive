---
title: "I messed up gnome!!!"
date: 2008-12-25
forum: General Help
---

### Post by TBSN on 2008-12-25
Hi all,

I was trying out the eye-pleasing compiz desktop (with the cube and the prettier alt-tabbing) and I seemed to have messed something up when I uninstalled it. Now the windows don't have the top orange bar, alt-tabbing doesn't work...

I installed it according to this tutorial:
[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-8.10-nvidia]("http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-8.10-nvidia")

I liked compiz, but I have a laptop that isn't really powerful enough to use it so I wanted it back to the way it was.

I went into the package manger and uninstalled anything that said "compiz" in the description. Now I can't alt-tab unless I am using the "extra" setting in System> Appearance> Visual Effects.

Could anyone tell me a way to make sure I have all the necessary gnome/ window packages, and delete any ones that I installed with compiz "simple-ccsm"?

I basically want the windows and appearance (that's what gnome is, right?) to be exactly as it was when I installed Ubuntu...

Should I reinstall Ubuntu?

Thanks for any help

---

### Post by inxygnuu on 2008-12-25
what is messed up?

---

### Post by xjcannonx on 2008-12-26
Did you try checking System-->Preferences-->Keyboard Shortcuts 

and scroll down to the window management section and make sure the shortcut you want is set up

---

### Post by utnubuuser on 2008-12-26
re-start x >>  Ctrl+Alt+backspace

---

### Post by TBSN on 2008-12-26
A couple things are messed up: the top of the windows are sometimes not there, the alt-tabbing is not working, and also I'm concerned that I uninstalled parts of the gnome package that were not installed when I installed the Compiz thing as per the tutorial...

I don't know how I would know what was originally installed on the system and what was not, so I am thinking about a reinstall...

---

### Post by Unlearned on 2008-12-26
look at go to system >preferences>advanced desktops effects settings

one of the options is window decoration. make sure this is checked

this happened to me and that was the problem :)

---

### Post by TBSN on 2008-12-26
Unfortunately, I don't have the advanced desktop effects settings (or anything similar) under preferences...:confused:

---

### Post by caleb12 on 2008-12-26
What about launching synaptic package manager and doing a search for Compiz - then uninstalling, then search gnome - and install (or reinstall) the metapackages for the desktop... and metacity as well (that's the default gnome window manager). 

Compiz isn't going to affect the gnome desktop, it doesnt replace any packages so your gnome install should be fine. Just disable compiz and make sure that metacity is your window manager and that's the default. 

If there are other issues like Alt+Tab, then check the global shortcuts for Gnome...

---

