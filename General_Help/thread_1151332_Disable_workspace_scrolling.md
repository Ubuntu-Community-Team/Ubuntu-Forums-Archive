---
title: "Disable workspace scrolling"
date: 2009-05-06
forum: General Help
---

### Post by Vacuum Tube on 2009-05-06
Hi All,
My first thread here. I a relative newcomer to ubuntu.

While trying out the different buntu distros, I came across the ability to disable the use of the scroll wheel to change workspaces in KDE (just use the kb shortcuts).

I'd like to do the same thing in gnome, but I can't figure out how using ubuntu 9.04.

Any suggestions?

TIA!

---

### Post by Therion on 2009-05-06
If you don't already have compizconfig-settings-manager installed, install it now with this command in the Terminal:```
sudo apt-get install compizconfig-settings-manager
```

Once you have it, go to System/Preferences/Advanced Desktop Effects Settings.
Select the Desktop category.
Click on the "Viewport Switcher" icon.
Click on the Edit icon next to Button5 (Move Next entry),and change the value to "None".
Click on the Edit icon next to Button4 (Move Prev entry), and change the value to "None".

Your scroll wheel will no longer do a "Move Next" or "Move Prev".

---

### Post by Meow27 on 2009-05-06
simple way = system->Preferences->appearance

click on the last tab, and make sure you have no visual effects

that should solve your problem, but also take take some of the eye candy off :/

---

