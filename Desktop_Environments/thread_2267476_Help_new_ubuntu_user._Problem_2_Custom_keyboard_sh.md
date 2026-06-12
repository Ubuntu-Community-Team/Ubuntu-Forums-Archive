---
title: "Help new ubuntu user. Problem 2: Custom keyboard shortcuts in Ubuntu 14.04."
date: 2015-03-01
forum: Desktop Environments
---

### Post by hey2 on 2015-03-01
Hi. 

First and foremost i like to apologize for my English level. I will try my best to describe my problem.

Can anybody tell me if it's normal for the custom keyboard shortcuts to not work properly in this version?

I tried installing and using the live Usb in this and another computer and all seem to show the same symptom.

When i clear the shortcut it continues to work and when i choose another key combination it doesn't work or work for i little moments.

I tried to restart and log out but it doesn't seem to do anything.

My main objective is to "hide all windows" using Super+d instead of Ctrl+Super+d 

Thank you

---

### Post by CantankRus on 2015-03-01
Using **compizconfig-settings-manager** (ccsm) there are 2 places to set show desktop.
In the Ubuntu plugin...
[ATTACH=CONFIG]260378[/ATTACH]

or in the general options plugin which is the same setting as in keyboard shortcuts (disabled by default)....
[ATTACH=CONFIG]260379[/ATTACH] [ATTACH=CONFIG]260380[/ATTACH]

I would say using just Super+d is unreliable in Unity because of how the Super key is used.
Seem to remember it was once "Super+d" but was changed to "ctrl+Super+d"

---

### Post by hey2 on 2015-03-02
Hi.

Thank you very much for your response.

I'm trying to avoid installing more software and stick to the basics in the beginning.

I don't know if i understood correctly what you said, but since you recommended another program does this mean that this feature is broken in 14:04?

On mine installation and in the Live USB the default it's not disabled, is Ctrl+Super+d. When i disabled it or try to change it, it  continues to work (ctrl+super+d).

When you say that is unreliable to use the super+d, are you saying that it conflicts with another shortcut? I would like to change because it seems logic to me use super+d and super+w to control the windows.

Thanks again.

---

### Post by CantankRus on 2015-03-02
compizconfig-settings-manager is just an application to change the settings of the Ubuntu window manager (compiz).
Any changes you make can easily be set back to default.
The Unity interface is a plugin for compiz.
 
The Unity shortcut for "show the desktop" is a different setting than the one shown in keyboard shortcuts.
You can try to change the shortcut using ccsm but I'm pretty sure there is a reason it was changed to ctrl+Super+d

---

