---
title: "can't switch keyboard layout with keyboard in XUbuntu :-(("
date: 2007-01-16
forum: Desktop Environments
---

### Post by lorap on 2007-01-16
thanx

---

### Post by Pobega on 2007-01-16
Applications -> Settings -> Keyboard Settings

---

### Post by lorap on 2007-01-17
i've already done that...
but there's nothing to do there.
the default option's already choosed with some shortcuts that don't relay to what i need...
my question's why i can't switch layout with a keyboard...
moreover,everything there's disabled...
let's say i can make it enabled,but how can i cause the OS switch the keyboard layout once i use something i add there...
1 of possibilities's:

/etc/X11/xorg.conf

but it depends on the keyboard type...
i've hp compac nx9010
thanx again

---

### Post by nikzeno on 2007-01-17
If you add the Keyboard Layout Switcher applet to your panel and you'll modify the xorg.conf adding the layout you want to use, for example mine is:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
**Option "XkbLayout" "it,se"**
Option "XkbOptions" "lv3:lwin_switch"
EndSection

then you'll be able to switch the layout with your mouse, by clicking on the flag of the applet.

I don't know how to assign a keyboard shortcut to the command.

By the way, this works well for me for all the xfce apps and external apps such as Opera, Ooo or Skype, but i have a strange behaviour in KDE apps (kopete and kmail). If I type this charachters:
 èòàù åöä'
 i got this in turn: 
Ã&#353;Ã²Ã Ã¹ Ã¥Ã¶Ã&#8364;'

Does anyone know how to fix this?

---

### Post by lorap on 2007-01-17
thanx again friends!
i've no prob switch it with the mouse keys.
i just want tp switch it with the keys of keyboard.
say alt+alt like in gnome.
i've already tried to change config,but it did nothing...
thanx

---

### Post by night-hawk on 2007-01-24
This is a bit late but maybe will be helpful to others.  Thanks to google here's how I did it

```
sudo mousepad /etc/X11/xorg.conf
```

Find this part:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us**,latam**"
	Option		"XkbOptions"	"**grp:alts_toggle,grp_led:scroll**"

The bolded text is what I added.
latam  = Latin American
grp:alts_toggle =  Both Alt keys together change the keyboard layout.
grp_led:scroll = Scroll LED lights up when the second layout is active.

Interestingly, the values for keyboard layouts and other keyboard options are in the file

```
mousepad /usr/X11R6/lib/X11/xkb/rules/xorg.lst
```

If you don't know your layout code you can search for it in the file above (scroll down to where it says "! layout").

---

### Post by MasterOfMuppets on 2007-02-11
I tried this on my Kubuntu, and it doesn't work... :(
I can switch from English to Hebrew, but not the other way around...

---

