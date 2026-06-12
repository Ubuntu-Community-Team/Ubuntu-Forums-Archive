---
title: "Lost Window Panes at Enable Desktop Effects"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by johnnybgood115 on 2008-03-06
All, 

I have enabled Desktop Effects on a new installation of Ubuntu 7.10 Gutsy Gibbon.  However, when the effects are enabled, I lose control of how many desktops I can have and it defaults to 1 desktop.  I have tried to increase the number of columns and rows by right-clicking on the desktop pane in the lower right corner but this does not add any desktops.  

Is there something blocking me or do I need to add desktops through some type of compiz control panel? 

Thanks in advance, 

Johnnyb

---

### Post by chewearn on 2008-03-07
Run this to install the compiz configuration (CCSM):
```
sudo aptitude install compizconfig-settings-manager
```

Then, access it via:
Panel Menu > System > Preferences > Advanced Desktop Effects Settings

First, make sure to do this in the CCSM, else any change you make might not get saved:
Click on the Preferences at bottom Left of the CCSM dialog.
Under Profile, click on [+] button, and enter a name.
Under Backend, choose "Flat-file Configuration Backend"
Click [Back] to go back to main view.

Then, the option to change number of desktops are located in:
General Options > Desktop Size

---

