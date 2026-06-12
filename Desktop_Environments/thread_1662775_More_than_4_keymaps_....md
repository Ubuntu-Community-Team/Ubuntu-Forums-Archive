---
title: "More than 4 keymaps ..."
date: 2011-01-08
forum: Desktop Environments
---

### Post by soig22 on 2011-01-08
Hi,

I currently use 4 keyboard maps in my session (Russian, Ukrainian, Polish and French). I'd like to use one more : Sweddish, but it seems that I can't have more than 4. Does anybody knows a way to bypass this limit ?

Many thanks,

Soig.

---

### Post by Krytarik on 2011-01-08
Right now it seems impossible to set up more than 4 keyboard layouts in gnome, at least in it's own preferences.

But you could workaround this by setting the keyboard layout directly, with a custom GUI, which makes use of "gconftool-2". I wrote a script for such a GUI for different purpose, you may just modify it:
[http://ubuntuforums.org/attachment.php?attachmentid=175620&d=1289759286](http://ubuntuforums.org/attachment.php?attachmentid=175620&d=1289759286)

The gconf-path is: /desktop/gnome/peripherals/keyboard/kbd/layouts

To lookup the values of your currently set up layouts, enter in a terminal:
```
gconftool-2 --get /desktop/gnome/peripherals/keyboard/kbd/layouts
```
or press Alt+F2, enter "gconf-editor", and browse down the path.

The actual command to set the layout would be like this:
```
gconftool-2 --set --type list --list-type string /desktop/gnome/peripherals/keyboard/kbd/layouts [us]
```

You will notice that your currently set value contains more than one entry. This only works in combination with Gnome's build-in preferences. If the value contains only one entry, those gets used by Gnome automatically, I've tested it.

Feel free to ask, if you need further help to implement it!

Greetings.

---

