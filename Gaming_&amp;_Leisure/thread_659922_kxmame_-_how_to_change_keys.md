---
title: "kxmame - how to change keys ?"
date: 2008-01-06
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2008-01-06
The default keys for kxmame are really bad and I would like to change them.
But I see no option to do so.
How can I change the keys ?
Or should I use other mame program ? what do you recommend ?

---

### Post by disturbedite on 2008-01-06
have you checked the config file?  if there aren't any key config options in the gui, then perhaps they are in the config file...

btw, i'd recommend sticking with kxmame, its still the best frontend imho.

---

### Post by MaximB on 2008-01-06
> **disturbedite said:**
> have you checked the config file?  if there aren't any key config options in the gui, then perhaps they are in the config file...

btw, i'd recommend sticking with kxmame, its still the best frontend imho.

nop, can't find it
no GUI options no config file..it just uses the default.

---

### Post by MaximB on 2008-01-06
I have managed to make some progress
I could save my keyboard configurations inside the game (while I play) but if I restart the game or quit the configurations are NOT saved.
I've tried to save via cards and state but to no avail.

If anyone managed to save the keyboard configurations please tell me how.

---

### Post by DoktorSeven on 2008-01-06
I assume you're talking about the controls for the games in XMame, not for the GUI KXMame (KXMame is only a frontend for the actual program that plays the arcade games, called XMame, and you only set the controls while playing the actual game.   Controls for the individual games won't carry over to other games, but setting default controls will).

If you're using plain XMame for your backend (Settings->Executable should show what you're using), make sure the path to the controller settings is writable by your user (Settings->Directories->Mame/Mess Additional Paths; by default it should all be in /home/[your user]/.mame subdirectories).  Check and see if these have accidentally been set with root permissions (e.g. by running xmame as root vi sudo without changing root's home path), if so, you need to change these back (**sudo chown -R [your username] /home/[your username]/.mame**, replacing [your username] as appropriate, without []s).

If you use SDLmame, you need to find and change mame.ini (sometimes in /etc, sometimes in ~/.mame/) and edit the CORE SEARCH PATH OPTIONS, particularly the ctrlrpath, to somewhere writable by your user.

Sorry for so much information presented in a random way, but hopefully this will give you some clue about where to look.  Ask for clarification if you still have problems.

---

### Post by MaximB on 2008-01-07
Thanks I've changed the paths and all for my SDL mame but still when I change the configuration inside the game via TAB (Input global) it still doesn't save.

The mame.ini file doesn't hold such configurations.
I don't know were else can I change the keyboard keys.
Still need help.

---

### Post by DoktorSeven on 2008-01-07
If you are using SDLmame then it *should* be that mame.ini or whatever your SDLmame is using.  You might have more than one INI file somewhere (~/.mame.ini, ~/.mame/mame.ini, /etc/mame.ini or it could be called sdlmame.ini ask well), and it could be in the CORE OUTPUT DIRECTORY OPTIONS as well (missed that earlier).  This is what SDLmame uses as its configuration, and if any of that is pointing somewhere that isn't writable, nothing will get saved.

---

### Post by MaximB on 2008-01-07
What do you mean by "CORE OUTPUT DIRECTORY OPTIONS" ? were is that ?
I know that I have changed the directories paths at settings>directories.
but it didn't help.

---

