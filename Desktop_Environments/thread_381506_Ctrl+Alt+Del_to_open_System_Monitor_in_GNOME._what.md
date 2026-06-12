---
title: "Ctrl+Alt+Del to open System Monitor in GNOME. what about beryl?"
date: 2007-03-11
forum: Desktop Environments
---

### Post by pjones0404 on 2007-03-11
i would like to know how to make this work in beryl. it works fine using metacity. can i just change the reference of metacity to beryl? or would it need to be emerald? i just dont want to mess anything else up.

thanks in advance.  

How to enable Ctrl+Alt+Del to open System Monitor in GNOME

    * Read #General Notes 

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

---

### Post by Waappu on 2007-03-11
Hi

Open Beryl Setting Manager and in General Options select Commands tab.
Type to Command line:1 ```
gnome-system-monitor
```
Then select Shortcuts tab and expand commands.
Db click Run command:1 and press Grab Key button and then press Ctrl+Alt+Delete

---

### Post by pjones0404 on 2007-03-11
That worked.

Thanks alot. =D>

---

