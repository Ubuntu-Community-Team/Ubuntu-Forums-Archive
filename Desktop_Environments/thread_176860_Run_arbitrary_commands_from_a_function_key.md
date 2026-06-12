---
title: "Run arbitrary commands from a function key?"
date: 2006-05-15
forum: Desktop Environments
---

### Post by Arndt on 2006-05-15
Is there a way to make, e.g., the F8 key, run an arbitrary command (script) of mine?

---

### Post by Ramses de Norre on 2006-05-15
```
gconf-editor /apps/metacity
```
Set the key in global_keybindings and the command in keybinding_commands.

---

### Post by Zombie process on 2006-05-15
even faster:

just change N for a number, increment it for each new command/script you add

$ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_N "your-key-combo"

$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_N "your-command-or-path-to-script"


example:

$ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><alt>F"
$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "firefox"

your example: 

$ gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 "F8"
$ gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 "~/myscript.sh"

;)

(by the way, the other post tells you how to do the same in a grafical way)

---

### Post by Arndt on 2006-05-16
Thanks, it works fine!

---

