---
title: "keyboard layout switching problem in xorg.conf"
date: 2009-01-06
forum: General Help
---

### Post by mirek on 2009-01-06
hello

today i decided to try xfce4 on my ubuntu 8.10 desktop installation. so - i installed it, tried and started to customize to my needs. and because i am not english, i need keyboard switching, so i found the panel applet, but no configurable keyboard shortcut for it. so - low level configuration of xorg.conf started.

my configuration looks like this:

```
Section "InputDevice"
   Identifier "Generic Keyboard"
   Driver "kbd"
   Option "CoreKeyboard"
   Option "XkbRules"    "xorg"
   Option "XkbModel"    "pc105"
   Option "XkbLayout"   "us,sk(qwerty)"
   Option "XkbOptions"  "grp:alt_shift_toggle,grp_led:scroll"
EndSection
```

it looks nice, but it's not working. strange  thing is, when i configure the core keyboard to use only slovak language, it's not working too:

```
Section "InputDevice"
   Identifier "Generic Keyboard"
   Driver "kbd"
   Option "CoreKeyboard"
   Option "XkbRules"    "xorg"
   Option "XkbModel"    "pc105"
   Option "XkbLayout"   "sk"
EndSection
```

i am confused about this. if i try this configuration by the hand with setxkbmap, it's working like a charm:

```
setxkbmap  -option grp:alt_shift_toggle,grp_led:scroll "us,sk(qwerty)"
```

log of Xorg looks ok, only on the console are messages, which looks suspicious:

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

so - any help? maybe i overlooked something and the problem is as usual - somewhere between the keyboard and chair, so - any i will appreciate any help.

thanks

mirek

---

### Post by abom on 2009-04-25
Try to add this command:
```
setxkbmap  -option grp:alt_shift_toggle,grp_led:scroll "us,sk(qwerty)"
```

to startup.

may be [this doc]("http://wiki.archlinux.org/index.php/Startup_files") form arch linux will help you.

---

