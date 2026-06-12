---
title: "Add new shortcut using keyboard shortcuts"
date: 2009-02-14
forum: General Help
---

### Post by Arenlor on 2009-02-14
I'm wondering if it's possible to add new shortcuts to that list, as I want to add a shortcut for firefox.

---

### Post by geirha on 2009-02-14
If my memory is not mistaken, one used to be able to do that in System -> Preferences -> Keyboard shortcuts, but apparently not anymore.

The options still exist though, they're just not settable through those regular GUIs.

Hit Alt+F2 to get the run dialog, and run «gconf-editor»
Set /apps/metacity/keybinding_commands/command_1 to "firefox"
Set /apps/metacity/global_keybindings/run_command_1 to the desired keyboard shortcut. The description of the key explains the syntax.

---

### Post by beren.olvar on 2009-02-14
to add a shortcut you have to:

-from a terminal, start gconf-editor
-go to apps->metacity
--in keybinding_commands add a command to run, in your case you can put in "command_1" firefox
--now in global_keybindings you have to find "run_command_1" and put the key binding you want to use, for example <Alt>F7 o something you want

that way you have about 12 keybindings you can personalize.

hope it helps
cheers!

EDIT: lol, too late... nvm

---

