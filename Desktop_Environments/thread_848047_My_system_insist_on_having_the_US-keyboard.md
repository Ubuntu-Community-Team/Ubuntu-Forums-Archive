---
title: "My system insist on having the US-keyboard"
date: 2008-07-03
forum: Desktop Environments
---

### Post by Archmage on 2008-07-03
I have a strange problem. When booting the live-cd I was choosing the **German-DE** Keyboard. I did install from it, did restart and did find out, that Xubuntu is using the **English-US** Keyboard considering X-Windows. If I switch via CTRL-ALT-F1 to the console I find there the **German-DE** Keyboard.

I fid find no easy solution to change the keyboard in X-Window, therefore I did go to the settings in Xubuntu and switch there on using the keyboard setting to **de**.

Than I did have the **German-DE** Keyboard.

However after a restart I again have the **English-US** keyboard.

If I go in the keyboard settings it is still switch to **de**. I did have to switch on use the X-Window-settings and than switch agaion on using the **de**-settings. Than I finally have my **German-DE**.

Is there a way to get rid of this problem? Maybe using the **German-DE**-keyboard in X-Windows? All the old ways to change them will manipulate the X.ORG-Settings and therefore on a update they wont be changed, because the X.ORG.Conf had been changed and therefore e.g. I wont have the benifits of a new monitor.

---

### Post by jensman on 2008-07-13
I am having a similar problem in Gnome. You can run

xmodmap /usr/share/xmodmap/xmodmap.de

at login to get your keyboard working correctly. This is not a perfect solution, but at least it's working. ;)

---

### Post by coffeecat on 2008-07-13
If you edit xorg.conf yourself I'm sure it won't get changed after an update. Could you post the contents of your /etc/X11/xorg.conf file?

The relevant section from mine (actually from Linux Mint with my laptop at the moment, but it should be the same as Ubuntu) is:

```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection
```You could try that but substitute <Option "XkbLayout" "de"> for <Option "XkbLayout" "gb". That ought to work.

I was trying to get various versions and flavours of Linux to configure a UK Apple keyboard for my Desktop computer. The GUI tools in Gnome and KDE worked fine, but I couldn't find anything in the Xfce versions I tried and modifying xorg.conf was the only way that worked for me.

---

