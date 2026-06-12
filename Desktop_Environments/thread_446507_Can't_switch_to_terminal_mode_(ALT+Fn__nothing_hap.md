---
title: "Can't switch to terminal mode (ALT+Fn  nothing happens)"
date: 2007-05-17
forum: Desktop Environments
---

### Post by hobbes_ba on 2007-05-17
Hi Folks,

i was trying to properly display portuguese graphical accents on text mode Ubuntu Feisty AMD64, for that i used dpkg -reconfigure console-setup and console-data to achieve it.

But, when i restarted my PC to make sure everything was working fine i noticed my GNOME stopped to switch ALT+FN to text mode and messed up my keyboard settings.

It used to work without problems on GNOME. 

GNOME Keyboard settings has a Unknown keyboard model and a US layout

user@feisty:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""

user@feisty:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 overrideSettings = true
 options = []

Any ideas?

---

### Post by AnRa on 2007-05-17
Did you try with Ctrl + Alt + Fn?

---

### Post by hobbes_ba on 2007-05-17
> **AnRa said:**
> Did you try with Ctrl + Alt + Fn?

Thanks for replying.

I[LEFT]t`s not working anymore, CRTL + ALT + FN stop working when i changed my keyboard layout on console mode, like i said on the first post
[/LEFT]

I need to restore my keyboard on GNOME to Brazilian ABNT2.

Anyone?

---

### Post by hobbes_ba on 2007-05-19
When i try to run dpkg-reconfigure console-setup i got this message at the end.

ckbcomp: Can not find file "rules/xorg" in any known directory

I guess there is something to do with my problem.


Anyone

---

