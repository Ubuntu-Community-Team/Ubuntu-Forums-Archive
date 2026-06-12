---
title: "More that 12 keybindings in gconf-editor"
date: 2010-05-22
forum: Desktop Environments
---

### Post by ZarlacMing on 2010-05-22
Hi,

While trying to setup keybindings i successfully has setup 12 of them, but I would like to have more, 22 to be exact.
I tried to add a new keybinding like this, but it won't work:

1. I ran gconf-editor
2. Browsed to /apps/metacity/keybinding_commands
3. Right clicked and clicked "Add new key" and entered the name command_13 with the type String and Value /home/myname/script/myscript
4. I the browsed to /apps/metacity/global_keybindings and added in the same way a new run_command_13 as a String and a key combination (ie. <Control><Alt>W).
5. But when I then clicked on run_command_13 to view the description, key name, owner there is an error message saying "There is no valid schema for this key". The same error message is shown for the keybinding_command command_13.
6. So, I thought i'll just apply the same schema as the other keys have, like this:

gconftool-2 --apply-schema /schemas/apps/metacity/keybinding_commands/command /apps/metacity/keybinding_commands/command_13

gconftool-2 --apply-schema /schemas/apps/metacity/global_keybindings/run_command /apps/metacity/global_keybindings/run_command_13

The error message is gone, but the keymapping still does not work.

Any ideas? Is there a log file that could contain some useful information?

---

### Post by ZarlacMing on 2010-05-22
Never mind. Found a workaround:

```
gnome-keybinding-properties
```

With that I could add the additional keybindings.

---

