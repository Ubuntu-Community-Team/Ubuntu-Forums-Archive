---
title: "delete the last remaining panel"
date: 2010-03-01
forum: Desktop Environments
---

### Post by raaj_bharath on 2010-03-01
[COLOR="RoyalBlue"]I am really eager to keep my desktop very clean  , very clean in the sense i do not want the panels [both of them] .Though i am successful in removing the bottom panel easily ,the option of removing the top panel seems greyed out[inaccessible] is there any solution ?

on googling the options i tried to use gconf editor
in 

gconf editor->session->required components->[right click] on panel ->edit and there delete 'gnome panel'

though this works once , after reboot the entire gnome menu session is off , ie the mouse right click doesnt work anymore .

is there a way to delete the panels in a safe manner ?[/COLOR]

---

### Post by lordjubblydave on 2010-03-01
right click the panel and select delete this panel

---

### Post by raaj_bharath on 2010-03-01
but that option is disabled !

---

### Post by lordjubblydave on 2010-03-01
Oh sorry, my mistake

---

### Post by lisati on 2010-03-01
As an alternative, I'd suggest "autohide"

---

### Post by MooPi on 2010-03-01
```
sudo  chmod -x /usr/bin/gnome-panel
```
Reboot

---

### Post by raaj_bharath on 2010-03-01
what does this command do ?
i guess it makes the panel completely transparent - am i right ?

---

### Post by stinkeye on 2010-03-01
.

---

### Post by nothingspecial on 2010-03-01
It makes the binary unexecutable so it will not run.

If you ever want the panel back, reverse it.

---

### Post by Rajan_92 on 2010-03-01
At least one panel is necessary in gnome desktop you cannot delete the last panel left.
One way is to uninstall gnome desktop but uninstalling it removes many other features too so first Google about it then take the right step and you can use k-desktop so its your choice.
By the way why do you want to remove everything from desktop.

---

### Post by nothingspecial on 2010-03-01
> **Rajan_92 said:**
> At least one panel is necessary in gnome desktop you cannot delete the last panel left.


Incorrect

[ATTACH]148664[/ATTACH]

The way I do it is ```
sudo mv /usr/bin/gnome-panel ~/.panel
```

That way if I ever want it back I can

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

Bare in mind, before you do this that Alt F1 and Alt F2 will cease to work and unless you going to run a lot of things from terminal it might be an idea to have gnome-do or kupfer installed.

---

