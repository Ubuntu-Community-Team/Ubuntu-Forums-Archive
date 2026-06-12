---
title: "Problems with Latin America keyboard"
date: 2005-10-06
forum: Desktop Environments
---

### Post by waltervalderrama on 2005-10-06
Hi everybody. Can some one help me with this. Suddenly my keyboard configuration changed and an error appears when i login in gdm.

Error al activar la configuraci&#243;n XKB.
Podr&#237;a deberse a varias circunstancias:
- un fallo en la biblioteca libxklavier.
- un fallo en el servidor X (utilidades xkbcomp, xmodmap)
- Un servidor X con una implementaci&#243;n incompatible con libxkbfile

Datos de la versi&#243;n del servidor X:
The X.Org Foundation
60802000

Si informa de esta situaci&#243;n como un fallo, por favor incluya:
- El resultado de <b>xprop -root | grep XKB</b>
- El resultado de  <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

In english is something like this

Error activating XKB config
I could be because of:
- a libxklavier library failure
- X server failure (xkbcomp utilities, xmodmap)
- X server with implementation not compatible with libxkbfile

I dont know what to do, please its driving me crazy, i cannot use my numerical keyboard. I cannot type latin america characters like "n" u know what i mean. The worst thing is that i cannot use "@" since my Alt GR key does'nt work.


I forgot, i tried using dpkg-reconfigure xserver-xorg, didnt work
When i try with System / Preferences / Keyboard gnome application crashes.

---

### Post by Ampersand on 2005-10-06
Did this happen after doing any updates or anything?

Try running the two comands listed ('xprop -root | grep XKB' and 'gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd'),  are the layouts and keyboard models listed correct in both cases?

---

### Post by waltervalderrama on 2005-10-06
Nop i think.

andre@valderrama:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""


andre@valderrama:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = pc105
 overrideSettings = false
 options = []

One is showing "us" configuration with 101 keys, and the other one 105 keys.

---

### Post by Ampersand on 2005-10-06
Try running the configuration editor (in the System menu, under preferences), then browse through the folders until you get to /desktop/gnome/peripherals/keyboard/ and change the value of 'layout' from '[]' to '[us]'.

---

### Post by waltervalderrama on 2005-10-06
Sorry to ask such a thing man, but i am running ubuntu in spanish, and cant find something similar to 'configurtion editor' in the system menu (preferences). There is an option called "Teclado" (keyboard). do you mean this??? Please be more specific, where is it (next to what option) or how is the icon. Sorry.....

---

### Post by Ampersand on 2005-10-06
The command for it is 'gconf-editor' if you want to run it from a terminal (probably easier (: ). For me, the icon is the front of a car and a spanner, although it might be different for you if you're using a different theme.

---

### Post by waltervalderrama on 2005-10-06
i did what u told me. Changed the layout to 'us'. I rebooted the system and the error dissapeared. I tried to change back my keyboard configuration to 'la'. The error appeared again. I changed used gconf-editor to change the keyboard layout to 'us' again. But when rebooted, gnome does not start. I am in the login screen, type user and passwd. But my desktop does not load.

Help, how can i save my system, I cannot open a console because my ALT key doesnt work. No CTR+ALT+F1 .... F6
How can i change my keyboard configuration to la again.....:confused: :confused: :confused: :confused: :confused: :confused:

---

