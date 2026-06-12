---
title: "[SOLVED] Kubuntu: Compose key and laptop hotkeys"
date: 2008-02-11
forum: Desktop Environments
---

### Post by sergiom99 on 2008-02-11
Hey there,
I am trying to enable my laptop's LeftWin key to act as a compose key to type my locale spanish characters. I managed to enable this at "K\Systems settings\Local\Keyboard-> Xkb options".

But when I did that, my laptops media hotkeys stopped working.
I only got them back when I disabled Xkb options and restarted X.

Anyone knows how to enable the compose key without messing all my keyboard settings?
thanks a lot!

---

### Post by linuxmagick on 2008-02-11
Depending on the make/model of your laptop, KDE may have a keyboard layout for you.  In the Control Center, see if you have a category for Regional and Accessibility ==> Keyboard Layout.  If you see that, then you can choose to enable keyboard layouts and see if your laptop is listed in the drop down list under where it says keyboard model:.  Then you can use the keyboard shortcuts section of Control Center to modify the actions of specific keys.  Sorry if these directions aren't completely accurate as I'm not currently using Ubuntu, but I figure that it would at least be similar since we are both using KDE.

---

### Post by sergiom99 on 2008-02-12
Thanks for your answer, I have an HP DV6646, but none of this product line are listed there.
I'll keep trying.

---

### Post by sergiom99 on 2008-02-20
any ideas on this one?

---

### Post by sergiom99 on 2008-06-06
just upgraded to HH.
Laptop multimedia-keys worked out-of-the-box, but If I enable "Xkb options" and then I set Left Win as compose key, multimedia keys stop working.
How can I use both??

---

### Post by sergiom99 on 2008-06-08
Solved adding this to my xorg.conf file:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection

```
cheers!

---

