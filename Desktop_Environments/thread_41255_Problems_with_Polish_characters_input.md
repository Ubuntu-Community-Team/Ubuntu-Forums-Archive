---
title: "Problems with Polish characters input"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Tomasz on 2005-06-12
This is my second ubuntu installation (first on this laptop though). Everything went fine, but this time I can't seem to get Polish characters with the usual right-alt+character combo. Locales are set ok (pl_PL UTF-8), the keymap is set to Polish, what the heck am I doing wrong? I've tried with different keyboard types, but this changed nothing. This is a laptop so it doesn't have the usual 100-something buttons, but he right-alt is a standard button, nothing fancy. Works in windows, doesn't work here.... any help would be appreciated. It's a Uniwill N340S8 lappy (branded by Actina, Gericom and other companies, keyword being N340S8 ).

---

### Post by Krogen on 2005-06-12
I can't help you but...


Czesc!  :smile: Polak z USA tutaj :)

---

### Post by Poul on 2005-06-12
Hey mate
First of all let us know if it worked on any other distro (if ever installed). Then let us know what is detected in keyboard preferences layout tab (I presume you know where to find it) You might get what you want by trying to change keyboard model to one of those that are designed for diffrent laptops but don't blame me if something goes wrong. I'm just trying to help after all. An don't forget to make sure that polish layout is selected as default.

Ps: A tu z Londynu

---

### Post by Tomasz on 2005-06-13
This is the first linux on this lappy I've ever experienced, so I can't tell you if the rightalt worked earlier.
 
Right_alt is bound with ISO_Level3_Shift , is that ok?

In the meantime I even managed to activate the tvout, Tahoma clear-type fonts and various other things. Tweaked to the max. Ubuntu would completely rock if I could input Polish letters, what do you suggest me to do?

language-pack-pl, language-pack-pl-base and language-support-pl are installed. Locale is set to pl-PL UTF-8, keymap is set to Polish, experimenting with different keyboard types gives no result. Seriously, help! This will be in no way a production machine without these darn Polish characters, I need them bad.

```
dom@ubuntu:~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

```

---

### Post by Tomasz on 2005-06-13
I've located the problem. Th right-alt key phisically doesn't work. I tried cleaning the keyboard, no effect. 
 
How can I remap this key to the "windows" key?
 
Edit: Nevermind, I've managed.

---

