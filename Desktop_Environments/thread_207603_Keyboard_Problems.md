---
title: "Keyboard Problems"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Fysidiko on 2006-07-02
I'm having some trouble with the keyboard layouts in Dapper. I selected English UK in the install, but now can't type '£' (shift and 3) - it just comes out as 3. The windows key also doesn't do anything - on Breezy I could use win + B to change tracks in amarok, for example. 
I thought this might be a keyboard layout problem, so I tried going to system -> preferences -> keyboard and, sure enough, the layout I had had no win or  keys. But when I tried to change it to a layout with the keys I wanted - UK English - Two error boxes popped up. "Error activating XKB Configuration. It can happen under various circumstances: A bug in libxklavier library, a bug in X server, X server with incompatible libxkbfile implementation"

It also said to use the results of xprop -root | grep XKB and gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd as debugging information, so here they are:

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "uk", "uk", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "uk", "uk", ""

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [uk  uk,gb]
 model = pc104
 options = [grp grp:alts_toggle]
 overrideSettings = true

Can anyone help me with this?

Thankyou.

Edit: This part of /etc/X11/xorg.conf looked relevant:
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "uk"
    Option         "XkbVariant" "uk"
EndSection

uk uk is what shows up in the layout screen - I assume this is linked to this file. Do I need to edit the file instead of using the GUI tool?

---

### Post by woedend on 2006-07-02
as a temporary solution let me know if this command fixes your problem
setxkbmap -model pc105 -layout gb -variant basic

---

### Post by Fysidiko on 2006-07-02
That's sorted it, thanks.

---

### Post by Webspot on 2006-07-15
I just found this thread through searching as I have problems with my UK keyboard. That command line fix worked for me. But how do I make that the default when I start up my computer. It just goes back to the old layout when I restart

---

### Post by woedend on 2006-07-15
As far as making it default, don't exactly know...i'm not around to look at it.  But until someone chimes in this will do the trick for you. 

gksudo gedit /usr/bin/fixkeyboard
paste in this

#!/bin/bash
setxkbmap -model pc105 -layout gb -variant basic

save, close
then - 
sudo chmod +x /usr/bin/fixkeyboard


now you can add fixkeyboard to your startup(under session prefs).

---

### Post by Webspot on 2006-07-16
Thanks!

---

### Post by geezerone on 2007-04-22
I get the same problem when trying to add microsoft internet keyboard and although the pound sign wasn't working nor are the quick keys (back, forward, stop, search etc...)

Is this bug going to be fixed anyone know for us UK keyboard users?

---

### Post by geezerone on 2007-04-28
Anyone know?

---

