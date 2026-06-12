---
title: "Compiz not letting change settings"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by mikeric on 2008-04-14
i installed compiz and it was working fine. I then installed emerald and got it working, and now when i try to change any settings in compiz all the boxes are greyed and it wont let me change any.

---

### Post by tommyhakinen on 2008-04-14
are you using compiz-fusion and have CCSM installed. if yes you may try this :

> 
compiz --replace


then go to cssm and see if it can be changed.

---

### Post by Zorael on 2008-04-15
edit: First of all, make sure you have the **compizconfig-settings-manager** package installed.

Start ccsm. It should be someplace in your menu panels, but you can open a run box (Alt+F2) and enter ccsm there to start it manually.

*Make sure* you have set it to automatically handle activated plugins under Preferences, right-most tab or so. If not set thus, it will instead check the list there for which plugins to activate, rather than which plugins you checked in the normal view.

If this doesn't work, try exporting your profile (again, under Preferences), then **deleting** the .compiz directory under your home directory.
```
$ rm -r ~/.compiz
```
If it complains about you not having the needed permissions, prepend sudo, making it 'sudo rm'. Then start ccsm again, go to Preferences, change Configuration Backend to Flat-file, and import your exported profile. And, again, make sure you have set it to automatically handle plugins.

As a last resort, some would recommend you run compiz with superuser permissions (sudo), but I believe this will only make it load settings from the root user directory (/root) rather than from your home directory. As such, it will create a new profile with default settings, which should have the same effect as both of the above methods (since what's really wrong is likely the first mentioned setting), coupled with the drawback of your user not being able to change compiz settings without using sudo.

---

