---
title: "Shortcut for Firefox"
date: 2009-03-27
forum: General Help
---

### Post by xg7 on 2009-03-27
I'd like to create a nice, convenient shortcut to open the browser.  Please help.  Thanks in advance :)

---

### Post by mikewhatever on 2009-03-27
You can just drag the launcher (same as shortcut) from the menu to where you want it.

---

### Post by xg7 on 2009-03-27
I meant a keyboard shortcut, oops.

---

### Post by pastalavista on 2009-03-27
In System > Preferrences there is an app called Keyboard Shortcuts... or if you prefer command line.. alt-f2 and type ```
gnome-keybinding-properties
```

and if you don't have it installed ```
sudo apt-get install gnome-keybinding-properties
```

---

### Post by sekinto on 2009-03-27
Open gconf-editor and go to /apps/metacity/keybinding_commands.
Double click on one of the commands (ex. command_1) and enter the command you want the binding to execute (ex. firefox %u) as the value.
Go to /apps/metacity/global_keybindings.
Double click on the run_command_x where x is the number you chose before.
Type in the key combination you want to use to execute the command (ex. <Control><Alt>f).

Also if you want to launch applications using the keyboard I **highly** recommend downloading Gnome-Do, it is awesome. To launch Firefox for example I press Alt+Space f Enter, to launch Evolution I press Alt+Space e Enter... but it can be used for more than just launching applications, it can be used to open recent documents, start an IM convo with a contact, start an e-mail to a contact, make a Twitter entry, etc.!

---

### Post by xg7 on 2009-03-27
> **pastalavista said:**
> In System > Preferrences there is an app called Keyboard Shortcuts... or if you prefer command line.. alt-f2 and type ```
gnome-keybinding-properties
```

and if you don't have it installed ```
sudo apt-get install gnome-keybinding-properties
```

Thanks.  It's installed and right now the shortcut for launching a web browser is "XF86WWW".  

What the heck does that mean?

What would be a good shortcut that wouldn't mess with other programs, etc.?

---

### Post by xg7 on 2009-03-27
> **sekinto said:**
> Open gconf-editor and go to /apps/metacity/keybinding_commands.
Double click on one of the commands (ex. command_1) and enter the command you want the binding to execute (ex. firefox %u) as the value.
Go to /apps/metacity/global_keybindings.
Double click on the run_command_x where x is the number you chose before.
Type in the key combination you want to use to execute the command (ex. <Control><Alt>f).

Also if you want to launch applications using the keyboard I **highly** recommend downloading Gnome-Do, it is awesome. To launch Firefox for example I press Alt+Space f Enter, to launch Evolution I press Alt+Space e Enter... but it can be used for more than just launching applications, it can be used to open recent documents, start an IM convo with a contact, start an e-mail to a contact, make a Twitter entry, etc.!

That's pretty sweet

---

### Post by Locutus_of_Borg on 2009-03-27
xbindkeys is a good program for launching applications via keyboard

i use windows key + F for firefox

---

### Post by Agent ME on 2009-03-28
> **xg7 said:**
> Thanks.  It's installed and right now the shortcut for launching a web browser is "XF86WWW".  

What the heck does that mean?

What would be a good shortcut that wouldn't mess with other programs, etc.?
XF86WWW refers to the browser button that's on some keyboards. Obviously not all keyboards have this button, so you can change it to whatever you want instead.

---

