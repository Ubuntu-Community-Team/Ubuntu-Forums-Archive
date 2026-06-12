---
title: "super (win) key as modifier (beryl/GNOME)"
date: 2007-10-03
forum: Desktop Environments
---

### Post by katoodifaas on 2007-10-03
Hi,

I know this problem has been discussed before, but I haven't found a decent solution. I'm running Ubuntu 7.04 with GNOME and beryl [but metacity exhibits the same behavior]. Anyway, if I attempt to set a keyboard shortcut with the Super key as a modifier, the KB shortcuts dialog only accepts the Super key on its own.

I know the recommendations about modifying Alt/Win key behavior in the Keyboard Preferences dialog, but that doesn't work for me (e.g. if I choose "Meta is mapped to the Win-keys", the Win/Super key *does* become a modifier (Mod4) and I can use it in KB shortcuts, but they just don't work. For example, I can now assign Mod4+L to lock the screen, but actually using the combination has no effect whatsoever).

Has anyone found a solution to this?

---

### Post by glinsvad on 2007-10-03
You just edit the gconf database. It works like this:
gconftool-2 --type string --set KEY VALUE

In the terminal just run:
```

gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_15 "<Mod4>l"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_15 "gnome-screensaver-command --lock"

```

... or you can run gconf-editor and set the keys manually

EDIT: I've chosen index 15 for this command, but you might as well choose any other (two-digit) integer as long as "run_command_NN" matches "command_NN"

---

### Post by katoodifaas on 2007-10-03
Nope, that doesn't work.

---

