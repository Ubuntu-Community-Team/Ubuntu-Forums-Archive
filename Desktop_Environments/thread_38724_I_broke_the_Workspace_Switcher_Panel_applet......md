---
title: "I broke the Workspace Switcher Panel applet....."
date: 2005-06-01
forum: Desktop Environments
---

### Post by Kyral on 2005-06-01
I don't know how this happened, but I went to try out a new panel arragement in GNOME, so I wound up deleting my main panel with everything. I figured I didn't like the new arrangement so I tried to bring it back. Worked, mostly. Somehow the Workspace Switcher applet got broken. As in, I cannot configure it.

```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_7/prefs/display_all_workspaces' stores a non-schema value
``` 

Thats the error that the error msg gives me. Anyone have a clue what I did?

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=Kyral]I don't know how this happened, but I went to try out a new panel arragement in GNOME, so I wound up deleting my main panel with everything. I figured I didn't like the new arrangement so I tried to bring it back. Worked, mostly. Somehow the Workspace Switcher applet got broken. As in, I cannot configure it.

```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_7/prefs/display_all_workspaces' stores a non-schema value
``` 

Thats the error that the error msg gives me. Anyone have a clue what I did?[/QUOTE]
 I assume you tried removing it form the panel and then adding it again, right? 


Is there a file ~/.gconf/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces/%gconf.xml


If so, you may try removing it - then it will use the default schema.

---

### Post by RyaninZion on 2005-07-18
I am now having the same problem.  I tried removing the Workspace Switcher and putting it back, but no luck.  I don't have the file Alexander suggested looking for...

Anyone have any idea on this?

---

### Post by mike998 on 2005-07-18
Did you install the gaim flashing taskbar notification hack?  I did that and it broke my workspace switcher.

---

### Post by RyaninZion on 2005-07-18
[QUOTE=mike998]Did you install the gaim flashing taskbar notification hack?  I did that and it broke my workspace switcher.[/QUOTE]
 No, I do not have any such hack for Gaim installed.

---

### Post by RyaninZion on 2005-07-19
OK, I managed to fix it.  Not sure if there is a more official way of doing it, but this worked for me:

Go to Configuration Editor
Open apps > panel > applets > applet_16 (this last one may vary for others - just click on each one and check the value of bonobo_iid to see which applet you are on) 

In the prefs folder double-click display_all_workspaces and enter a value of 1.

---

