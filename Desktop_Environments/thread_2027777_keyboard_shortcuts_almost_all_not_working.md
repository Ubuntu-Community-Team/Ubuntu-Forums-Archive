---
title: "keyboard shortcuts almost all not working"
date: 2012-07-17
forum: Desktop Environments
---

### Post by jim.hitch on 2012-07-17
Have just completed a new install of xubuntu 12.04. 

I had kubuntu but have now install xubuntu on the / and left /home partition intact.

I prefer to use keyboard shortcuts where possible. Strangly a few of them are working (eg. Alt+F2 & Alt+F10) but others are not (eg. Ctrl+Alt+Del & Ctrl+Esc), and changing/adding shortcuts in settings doesn't work, though if I run the relevant commands in a terminal it works. Why is this?

Not sure if it's related, but the new install didn't automatically run xfwm4, though a single manual run seems to have fixed this.

Thanks.

---

### Post by LewisTM on 2012-07-17
Sounds like some of your configuration got corrupted.
You can go to the Settings Manager/Keyboard/Keyboard Shortcuts and reset default settings. If that doesn't work you will have to take more extreme measures.

Log out of Xfce. At the login screen press Ctrl-Alt-F1 and enter your username as password. Then run this command (better write this down):
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```
You can now go back to the login screen (Ctrl-Alt-F7) and return to Xubuntu. Hopefully the glitch will be gone.

Also note that more keyboard shortcuts can be found in the Window Manager/Keyboard settings. Some of those might conflict with custom ones; thankfully they can be changed. An example is Ctrl-F4 which is usually used for closing a document but in Xfwm4 is set for switching to Workspace #4.

Cheers!

---

### Post by jim.hitch on 2012-07-18
Many many thanks. Though I haven't had a chance to fix them all yet, and there still seems to be some confusion, you have put me on the right track.

I think the problem is that my old KDE shortcuts are still knocking about and confusing things, the other thing is that I've been using KDE for five years and am still learning the ropes with xfce.

---

### Post by w3chtml on 2012-12-24
> **LewisTM said:**
> Sounds like some of your configuration got corrupted.
You can go to the Settings Manager/Keyboard/Keyboard Shortcuts and reset default settings. If that doesn't work you will have to take more extreme measures.

Log out of Xfce. At the login screen press Ctrl-Alt-F1 and enter your username as password. Then run this command (better write this down):
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```
You can now go back to the login screen (Ctrl-Alt-F7) and return to Xubuntu. Hopefully the glitch will be gone.

Also note that more keyboard shortcuts can be found in the Window Manager/Keyboard settings. Some of those might conflict with custom ones; thankfully they can be changed. An example is Ctrl-F4 which is usually used for closing a document but in Xfwm4 is set for switching to Workspace #4.

Cheers!
Still have problem with hotkeys, not always rm helps me.
I'd Ubuntu with unity, than install xfce + remove unity.

Can somebody help me ?

-
Thanks

---

