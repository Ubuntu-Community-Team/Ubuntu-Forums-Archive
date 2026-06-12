---
title: "Mapping Windows Key and Cabinet Power Button"
date: 2012-04-23
forum: Desktop Environments
---

### Post by dzchimp on 2012-04-23
I'd like to Map the Windows Key to the KDE App Launcher; Win+E to Dolphin, Win+R to Konsole, all at the same time.

I'd like some help to figure this out.

---

### Post by dzchimp on 2012-04-23
I'd like to explain so far what I've tried to activate Windows Key as the key to activate Application launcher widget:

Found out the key code with:
```
xev | grep Super_L
state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES
```

Changed Mapping:
xmodmap -e 'keycode 133 = F13'

Global Keyboard Shortcuts>Plasma Desktop Shell>Activate Appln launcher widget>Custom>F13

It doesnt work yet.

---

### Post by rotave on 2012-04-24
To change the KDE app launcher shortcut right click on the launcher icon > Application Launcher Settings > Keyboard Shortcut (and change from there)
To configure custom shortcuts goto System Settings > Shortcuts & Gestures > Custom Shortcuts. You can add custom shortcuts from here. 
For example to add Win + E to Dolphin right click under Configure Input Actions Settings > New > Global Shortcut > Command/URL (give it a name) > Trigger (input shortcut) > Action > Command/URL (type dolphin in text box). Hit apply.

---

### Post by dzchimp on 2012-04-24
> **rotave said:**
> To change the KDE app launcher shortcut right click on the launcher icon > Application Launcher Settings > Keyboard Shortcut (and change from there)
To configure custom shortcuts goto System Settings > Shortcuts & Gestures > Custom Shortcuts. You can add custom shortcuts from here. 
For example to add Win + E to Dolphin right click under Configure Input Actions Settings > New > Global Shortcut > Command/URL (give it a name) > Trigger (input shortcut) > Action > Command/URL (type dolphin in text box). Hit apply.

Thanks. The first part worked, and I was able to open the App launcher with Win key. But when it's configured in this way, I'm unable to set Win+[some other key] for anything else, as it's being detected as a single key press, and a warning pops up stating that the key has already been assigned to the App launcher.

[IMG]http://droidzone.in/images/screenshots/Selection_004.jpeg[/IMG]

---

### Post by rotave on 2012-04-25
I forgot that KDE won't allow you to map the Win Key by itself and then have other Win+ shortcuts. You're going to have select a different key combination for the app launcher. Maybe something like Win+Space?

---

### Post by dzchimp on 2012-04-25
No wonder. Thank you.

---

