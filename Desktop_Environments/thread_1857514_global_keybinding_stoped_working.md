---
title: "global keybinding stoped working"
date: 2011-10-10
forum: Desktop Environments
---

### Post by idnael on 2011-10-10
Want to create a global keybinding to run a specific command.

Usually  that should be done in gconf-editor, inside node apps/Metacity. Just create entries in keybinding_commands/command_X and global_keybindings/run_command_X.

I found that it stopped to work, and I think it was after an recent upgrade! Anyone else had this problem?

---

### Post by Krytarik on 2011-10-10
> **idnael said:**
> Usually  that should be done in gconf-editor, inside node apps/Metacity. Just create entries in keybinding_commands/command_X and global_keybindings/run_command_X.
Picking up your wording; usually that should be done in "Keyboard Shortcuts". :P
At least I do so, as I'm not eager to bother with adding those GConf keys and values manually. However, sometimes I edit them afterwards via "gconf-editor", to circumvent the limitations of "Keyboard Shortcuts", particularly reg. the accepted key combinations.

Regards.

---

### Post by idnael on 2011-10-26
ah, that's better! 

Thanks a lot Krytarik

---

