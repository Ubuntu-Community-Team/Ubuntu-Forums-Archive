---
title: "ALT+F2 doesn´t work anymore"
date: 2006-03-29
forum: Desktop Environments
---

### Post by Kosmonaut on 2006-03-29
I´m a Kubuntuuser, I had initialy started with the Gnome-Desktop but *you know* I changed to KDE. ;-)
Last week I wanted to have an other look at Gnome. But the ALT+F2 doesn´t work in Gnome anymore. I have allready looked in the shortcut settings, it says that ALT+F2 should work. But it doesn´t- Every other shortcut works...That´s strange isn´t it?
What should I do now?

---

### Post by dcstar on 2006-03-29
[QUOTE=Kosmonaut]I´m a Kubuntuuser, I had initialy started with the Gnome-Desktop but *you know* I changed to KDE. ;-)
Last week I wanted to have an other look at Gnome. But the ALT+F2 doesn´t work in Gnome anymore. I have allready looked in the shortcut settings, it says that ALT+F2 should work. But it doesn´t- Every other shortcut works...That´s strange isn´t it?
What should I do now?[/QUOTE]
System-Preferences-Keyboard Shortcuts

"Show the panel run application dialog", set it to ALT-F2

---

### Post by Kosmonaut on 2006-03-29
Thanks for your answer!

But I have allready tried your suggestion. But it is *not* working....Sorry 
Even when I use ALT+F3 it is not working :-(...As I said every other shortcut works.:confused:

---

### Post by aysiu on 2006-03-29
Does Alt-F2 still work in KDE?

---

### Post by Kosmonaut on 2006-03-29
[QUOTE=aysiu]Does Alt-F2 still work in KDE?[/QUOTE]

Yes , without any problems.

---

### Post by aysiu on 2006-03-29
Maybe try this? ```
sudo apt-get update
sudo apt-get install --reinstall metacity
``` If that doesn't work, try digging around the hiddnen files in the /home/kosmonaut folder for anything with *metacity* in it. Delete stuff to do with keybindings.

---

### Post by Kosmonaut on 2006-03-30
[-( No, I´m afraid it doesn´t work...Any other hints?

---

### Post by Naneau on 2006-11-06
I'm having the same problem, I tried rebinding it to another key combination and reinstalling metacity, but I just can't get that handy window to pop up. I'm really missing it...

---

### Post by kutjara on 2008-04-01
For anyone still experiencing this problem (as I am), I found a workaround. I couldn't get Alt+F2 to work, but I did install the "Run Application..." applet in the Gnome Panel, which does the same thing.

Just right click on the panel, choose "Add to Panel..." then scroll down to "Run Application..." and select the applet. Now you have a button in your Gnome Panel with the same functionality as Alt + F2

---

