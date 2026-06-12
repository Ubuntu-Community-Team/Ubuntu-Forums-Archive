---
title: "Bind a key to a command?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by caviidae on 2006-06-06
My wife has a (annoying) backlight keybroad that works off of the scroll lock led. I figured out quickly that I can turn the light on and off with

xset led 3
xset -led 3

Making a toggle script isn't beyond me either...

But, How do you bind said script to a key?

Thanks for any help!

---

### Post by aysiu on 2006-06-06
Are you using KDE, Gnome, or XFCE?

---

### Post by Ivan Matveich on 2006-06-06
Run something like this:

```

gconftool-2 -s /apps/metacity/keybinding_commands/command_1 -t string 'xset led 3'
gconftool-2 -s /apps/metacity/global_keybindings/run_command_1 -t string '<Alt>F1'

gconftool-2 -s /apps/metacity/keybinding_commands/command_2 -t string 'xset -led 3'
gconftool-2 -s /apps/metacity/global_keybindings/run_command_2 -t string '<Alt>F2'

```

or set those keys with gconf-editor.

---

