---
title: "Changing Keyboard Layout Options via gconftool-2"
date: 2013-01-18
forum: Desktop Environments
---

### Post by leden on 2013-01-18
Since my laptop is often (dis)connected from the dock to which an Apple Keyboard is attached, I am looking for a convenient way to trigger some changes in keyboard layout through from the command line / script.

The effect I want to achieve is the same as going to System Settings -> Keyboard Layout -> Options ... and tick the "Left Alt is swapped with Left Win" under "Alt/Win key behavior".
After performing the above GUI operation, I can see that the command
```
gconftool-2 --get /desktop/gnome/peripherals/keyboard/kbd/options
```
Produces the following output:
```
[altwin	altwin:swap_lalt_lwin]
```

But, I want to achieve the same effect of via the command line instead. Therefore, I tried the following:
```
gconftool-2 --set --type=list --list-type=string /desktop/gnome/peripherals/keyboard/kbd/options "[altwin	altwin:swap_lalt_lwin]"
```
which should effectively achieve the same effect as above (and indeed running the above get command confirms this).

However, for some weird reason changes don't take effect (the key bindings are still unaffected), even though they are visible via both [FONT="Courier New"]gconf-editor[/FONT] or [FONT="Courier New"]gconftool-2[/FONT].
Moreover, when I go to the GUI the changes are not visible and if I am to make the change now the GUI crashes.

Any ideas why it does not work?

---

### Post by stinkeye on 2013-01-18
What release are you using?
In 12.10 setting is in dconf.Use dconf-editor or the gsettings command.
eg
Get current..
```
gsettings get org.gnome.libgnomekbd.keyboard options
```


Set "Left Alt is swapped with Left Win"...
```
gsettings set org.gnome.libgnomekbd.keyboard options "['altwin\taltwin:swap_lalt_lwin']"
```


Set back to default...
```
gsettings reset org.gnome.libgnomekbd.keyboard options
```

---

### Post by giant420 on 2013-03-14
Hate to bump this thread, but I am looking for the same solution and neither option is working for me. I am running 12.04 LTS. Neither ```
gsettings set org.gnome.libgnomekbd.keyboard options "['altwin\taltwin:swap_lalt_lwin']"

``` or ```
gconftool-2 --set --type=list --list-type=string /desktop/gnome/peripherals/keyboard/kbd/options "[altwin	altwin:swap_lalt_lwin]"
``` actually change anything.

---

### Post by stinkeye on 2013-03-14
The gsettings command works here in 13.04. and 12.10

What does dconf-editor show. (2nd pic)

---

### Post by giant420 on 2013-03-14
I don't know why it wasn't working before, it is now! Now I can easily alias a command to switch between my two keyboard layouts. Thanks for the help! 

Just to confirm,   

```
gsettings set org.gnome.libgnomekbd.keyboard options "['altwin\taltwin:swap_lalt_lwin']"
```

Does in fact work on 12.04 LTS.

---

