---
title: "can not change keyb layout"
date: 2009-02-27
forum: General Help
---

### Post by ottosykora on 2009-02-27
when I try to change keyb layout in ubuntu 8.04, I am getting following error msg and keyboard can not be changed:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
Colin Harrison
60900031

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by Icebear on 2009-02-27
How did you try to change the layout. 

This is how I added additional keyboards
goto
system>preferences>keyboard

Then hit the layout tab and hit add button


for changing the keyboard when in the layout tab hit the layout option button

then choose the layout switching and choose what key you want to use

if you want a keyboard indicator on the panel go to a empty space on the panel and click the right mouse button and choose "add to pannel"

then scroll down to keyboard incdicator

---

### Post by ottosykora on 2009-03-17
yes, when I do all what you say, it looks like it works, but no changes in keyb layout. On the next start of ubuntu, I am getting the above mentioned message.

---

