---
title: "[Keyboard layout] Always bad kbd layout in gnome, ok in console"
date: 2007-02-28
forum: Desktop Environments
---

### Post by GuiPoM on 2007-02-28
Hi everybody !

I have since yesterday a layout problem with both my gnome and my XGL sessions. I always had a layout problem with my XGL session (no alt-gr key). This problem is a known bug of XGL, I just have to execute a command to get back the right (xprop -root -f _XKB_RULES_NAMES 8s -set _XKB_RULES_NAMES xorg &&
setxkbmap -model pc105 -layout fr -variant latin9 ... for my french keyboard).

Yesterday, after an hard reboot (power cut :( ) I launched my XGL session and gnome asked me if I want to keep my X or gnome keyboard layout. I discovered this window for the very first time, I have selected gnome.

Now, even in my gnome session my keyboard layout is bad: it is azerty (youpi ! correct) but my numpad is not ok (no 5 key, no . key) and no alt gr key. I have no XGL module started, lsmod | grep xgl returns nothing ...

In this gnome session, which previously worked perfectly, I must now go to System>Preferences>Keyboard, swap french and english layout (two times, just to modify something, and my keyboard is ok.

In console (Ctrl+Alt+F*) keyboard is perfectly configured.
My xorg.conf seems to be correct, it is not modified:
```
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "fr"
        Option      "XkbVariant" "latin9"
EndSection

```

I have no idea what to set or modify, do you have some hints about what could be not configured correctly somewhere. I must have do something wrong, but I don't know what. Thanks

GuiPoM

---

### Post by GuiPoM on 2007-03-01
Is there any check I can do to understand what is not correctly configured :confused:

EDIT: I have to add that on gdm keyboard is working !!!

This must be a problem somewhere with gnome :confused: :confused: :confused:

---

