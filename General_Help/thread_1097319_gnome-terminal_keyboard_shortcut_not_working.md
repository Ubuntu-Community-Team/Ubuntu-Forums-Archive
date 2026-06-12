---
title: "gnome-terminal keyboard shortcut not working"
date: 2009-03-15
forum: General Help
---

### Post by rowbird on 2009-03-15
Hi all, i am trying to setup gnome-terminal hotkey without much success. I have tried system, preference, keyboard shortcut,open terminal window,and it doesn't do anything.
   I have also tried gconf-editor, apps/metacity/keybinding_commands/ and inserted gnome-terminal under command 1, then apps/metacity/global_keybindings,then entered <ALT>F12 under run_command_1, and marked them as default, aven under sudo, and it still didn't work. 
   I also tried installing Tilda, but the keyboard shortcut only works after i select it out of the main panel menu with the mouse, and same with Yakuake. Tilda also sat there processing a gksudo command until it ran out of memorty. I know that with linux you can get a machine to do almost anything, but this is starting to feel like a monumental task for something that i am sure is not that difficult. If someone knows a way to do this, i would love to hear from them. Thanks in advance.

---

### Post by rowbird on 2009-03-16
SOLVED. I got Tilda to auto start by putting it in under system, sessions, autostart programs, and added "tilda" in the Command box. I was making the mistake of entering the full path, and a capital T in the dialog box. All it needed was a small case "tilda" and that was it. I reinstalled Tilda and now it runs gksudo just fine, so i'm happy now.

---

