---
title: "Keymap"
date: 2005-12-07
forum: General Help
---

### Post by canadianwriterman on 2005-12-07
Does anyone know where I would find the keymap under Breezy? For some reason, my Delete key no longer works. 

I know there was a problem if you install the CTL-ALT-DEL utility through Automatix, but I don't think I have done that. I loooked in the keybindings settings and don't see anything about the delete key.

Thanks for your help.
[B]
EDIT: Found the problem, but not the total solution.[/B] I went to **System > Preferences > Keyboard Shortcuts** and found that, somehow, I had programmed the Delete key to perform "Sleep." Unfortunately, I can only change the Sleep function to another key (which gets my Delete key back!). I can't figure out how to set the Sleep key to "Disabled." It seems to want something in there. How to I set a Keyboard Shortcut at "Disabled?"  Thanks.

**EDIT: SOLVED In the Keyboard Shortcuts utility, you can disable a key assignment by highlighting the shortcut and hitting the backspace key.**

---

### Post by frodon on 2005-12-08
Have you read this thread ?
It contains useful informations which might help you : [http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

---

### Post by canadianwriterman on 2005-12-08
[QUOTE=frodon]Have you read this thread ?
It contains useful informations which might help you : [http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)[/QUOTE]

Yes, I did read that and several other threads when I was looking for the keymap. However, my question is a little different... it relates to the Keyboard Shortcuts utility under Preferences.

When you open the utility and look at the key assignments in this utility, you can see that some keys are "Disabled." I want to disable one of the keys, but can't figure out how you do that. The utility seems to want a key to be entered for the "Sleep" mode setting. My question is: how can I use this utility to set a function as "Disabled."

Thanks for your help!

---

### Post by frodon on 2005-12-08
Ok, you just want to disable a shortcut if i understand well.
I don't know how to do it with this utility, however (i'm not sure of that because i'm not in front of ubuntu) but in the Gconf editor under apps > metacity > global_keybindings or something like that you should find all the shortcuts definition, so putting in the right field the word "disabled" should fulfill what want to do.
Or maybe when the tool ask you to enter a shortcut the "echap" input set to "disabled" the function.

---

### Post by canadianwriterman on 2005-12-08
[QUOTE=frodon]Ok, you just want to disable a shortcut if i understand well.
I don't know how to do it with this utility, however (i'm not sure of that because i'm not in front of ubuntu) but in the Gconf editor under apps > metacity > global_keybindings or something like that you should find all the shortcuts definition, so putting in the right field the word "disabled" should fulfill what want to do.
Or maybe when the tool ask you to enter a shortcut the "echap" input set to "disabled" the function.[/QUOTE]

Thanks, frodon. I'm not in front of my machine either, but I'll try your suggestion when I get home tonight.

---

### Post by Michalxo on 2007-11-21
I've got 1 easier solution. Maybe its written somewhere else here, (and this topic is old for 2 years :) )
In gconf-editor edit this key ```
<Control><Alt>Delete
``` in
```
/apps/gnome_settings_daemon/keybindings/power
``` to anything you like (I did Delet, because It won't work for me either) and in 
```
/apps/metacity/global_keybindings
``` edit run_command_1 to```
 <Ctrl><Alt>Delete
``` and assign this keybind to command by ```
/apps/metacity/keybinding_commands
``` add to command_1 ```
gnome-system-monitor
```
That's It.  you can assign in xmms buttons too as you were used to use in winamp global hotkeys (xmms -h) ( ctrl+alt+ home/delete/insert/Prior(pgup)/Next(pgdn) )

---

