---
title: "'Initiate Windows Picker' Keyboard shortcut in GNOME"
date: 2011-07-16
forum: Desktop Environments
---

### Post by trivedia on 2011-07-16
Hi

I recently installed Ubuntu 11.04 and am using the Unity desktop manager (environment?). However, for remote access to my machine through vncserver, I found that if use GNOME desktop manager (by using gnome-session & in my ~/.vnc/xstartup), the performance is better.

This morning I wanted to use my <Super> + w key combination [as was the case in my GNOME environment in Ubuntu 10.04] to switch between windows. However, I found that the option to set this key combination through 'Initiate Windows Picker' under System->Preferences->Keyboard Shortcuts and the Desktop option therein was missing. 

I am not sure what is the way to get the 'Initiate Windows Picker' options in there when using GNOME. 

I tried CCSM (Compiz Configuration Settings Manager) too. There I found sever Initiate Picker settings (of differnt flavours) under the 'Scale' & 'Shift Switcher' options. None of them worked for me. I even tried modifying them, but my system was not responding.

Anyway systematic way to trouble shoot this will be much appreciated.

---

### Post by Krytarik on 2011-07-16
Try using the command like this, to first make sure that Compiz will be run:
```
gnome-session --session=classic-gnome &
```
Then, the window picker usually used by default in classic Gnome is the one from Compiz' "Scale" plugin.

Greetings.

---

### Post by trivedia on 2011-07-19
> **Krytarik said:**
> Try using the command like this, to first make sure that Compiz will be run:
```
gnome-session --session=classic-gnome &
```Then, the window picker usually used by default in classic Gnome is the one from Compiz' "Scale" plugin.

Greetings.

 I switched to using the gnome desktop environment and now when I log into the machine directly i.e. not using vnc, I can use the <Shift><Alt>Up keyboard shortcut to scale the windows. However, when I vnc into the machine using gnome-session, the keys do not work. 

Also, has something changed in Ubuntu 11.04 because of which the Initiate Windows Pickers options cannot be directly accessed from System->Preferences->Keyboard Shortcuts? I have to go the scaling option for CompizConfig Settings Manager to access the Ininitiate Windows Picker (from the Scale menu). Even there, I cannot seem to change the default setting of <Shift><Alt>Up. If I change by clicking on edit, the keyboard shortcut comes up as disabled.

Does anyone have any experience with this?

---

### Post by Krytarik on 2011-07-19
> **trivedia said:**
> If I change by clicking on edit, the keyboard shortcut comes up as disabled.
You don't have to click on the Edit button to change the shortcut, in fact, I would never do that, because it tends to break the shortcut completely. Instead just click on the button which states the current shortcut, then, in the upcoming dialog, click on "Grab key combination" to set another shortcut.

---

### Post by trivedia on 2011-07-20
> **Krytarik said:**
> You don't have to click on the Edit button to change the shortcut, in fact, I would never do that, because it tends to break the shortcut completely. Instead just click on the button which states the current shortcut, then, in the upcoming dialog, click on "Grab key combination" to set another shortcut.

Thanks for pointing that out. It worked. Thanks.

---

