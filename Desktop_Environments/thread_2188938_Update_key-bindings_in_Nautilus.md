---
title: "Update key-bindings in Nautilus"
date: 2013-11-19
forum: Desktop Environments
---

### Post by reef2dive on 2013-11-19
Does anyone know how the key-bindings in Nautilius and Gnome 3.x can be update / set.
<SHIFT DEL> works, while I need <CTRL DEL>
I can find documentation referring to Nautilus on Gnome 2 and it the setting is not available in dconf / apps / nautilus.

---

### Post by BrunoLotse on 2013-11-20
Hi:) When I have to change(add,modify,remove) key-bindings in Nautilus first I would execute```
gsettings set org.gnome.desktop.interface can-change-accels true
```Then I would run Nautilus, open window with existing key-binding and enter a new one. The old one would be gone and a new would be instead. Then I would lock keybindings```
gsettings reset org.gnome.desktop.interface can-change-accels
```Cheers,Bruno

---

### Post by cjhoward on 2013-11-26
[COLOR=#000000]"Then I would run Nautilus, open window with existing key-binding and enter a new one."


I don't fully understand this part.  Where are key bindings configured in/for Nautilus?  I was unable to successfully change and apply ~/.config/nautilus/accels after ticking the "can-change-accels" dconf option.  From the looks of the file header, it's only a dump (not an rc) anyway.

EDIT: Running Ubuntu 13.10 and Nautilus 3.8.2[/COLOR]

---

### Post by mc4man on 2013-11-26
> **cjhoward said:**
> [COLOR=#000000]"Then I would run Nautilus, open window with existing key-binding and enter a new one."


I don't fully understand this part.  Where are key bindings configured in/for Nautilus?  I was unable to successfully change and apply ~/.config/nautilus/accels after ticking the "can-change-accels" dconf option.  From the looks of the file header, it's only a dump (not an rc) anyway.

EDIT: Running Ubuntu 13.10 and Nautilus 3.8.2[/COLOR]
You can use that file (~/.config/nautilus/accels), just that any changes & or additions cannot have ; at start of line.
So for example the op's  - 
edit 
 ; (gtk_accel_path "<Actions>/DirViewActions/Delete" "<Shift>Delete")
to 
(gtk_accel_path "<Actions>/DirViewActions/Delete" "<Primary>Delete")

(then kill & restart nautilus
Or in the above case the orig could be left & a new added, in that case both would work

---

### Post by BrunoLotse on 2013-11-27
Hi:)I do not have accels file in ~/.config/nautilus. Yet I am able to change keybindings using gsetting command. When can-change-accels is set to true I am running Nautilus, open menu item, say Alt-F , and hover cursor over item I want to change. When it's highlighted I enter new key shortcut. It shows up immediately. Then - reset can-change-accels. That's all:) Nautilus --version 3.4.2Cheers,Bruno

---

### Post by BrunoLotse on 2013-11-27
Gee!!! I've found it:) On my system file with bindings ```
~/.gnome2/accels/nautilus
``` Thank you mc4man for inspiration:)Cheers,Bruno

---

### Post by cjhoward on 2013-11-27
Still can't get the key bindings to remap.  After ticking the dconf 'can-change-accels' option, I tried changing these two lines (with _and_ without leading semi-colons):

~/.config/nautilus/accels
(gtk_accel_path "<Actions>/ShellActions/TabsNext" "<Primary>]"
(gtk_accel_path "<Actions>/ShellActions/TabsPrevious" "<Primary>["

Save, then...

nautilus -q
Start file explorer from unity launcher.  Original key bindings remain.

---

### Post by mc4man on 2013-11-27
> **cjhoward said:**
> Still can't get the key bindings to remap.  After ticking the dconf 'can-change-accels' option, I tried changing these two lines (with _and_ without leading semi-colons):

~/.config/nautilus/accels
(gtk_accel_path "<Actions>/ShellActions/TabsNext" "<Primary>]"
(gtk_accel_path "<Actions>/ShellActions/TabsPrevious" "<Primary>["

Save, then...

nautilus -q
Start file explorer from unity launcher.  Original key bindings remain.
You can't use certain keys directly, you must use name, ex. / = slash, \ = backslash, [ = bracketleft, ] = bracketright
So one of yours - 

```
(gtk_accel_path "<Actions>/ShellActions/TabsNext" "<Primary>bracketright")
```

Note - The dconf option is meaningless in regards to editing the accels file

Edit: remember NO leading semi-colon, just as above

---

### Post by cjhoward on 2013-11-27
That worked!  Thank you!

---

