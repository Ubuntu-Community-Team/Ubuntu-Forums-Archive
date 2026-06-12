---
title: "How to repair Workspace Switcher applet"
date: 2006-01-25
forum: Desktop Environments
---

### Post by caldico on 2006-01-25
Sorry for my english, is not my native tonge........

Hi: I want to install this applet into my panel (where Applications, Places and System Menus resides)...after doing using " Add to Panel" , looking the applet and selecting it, everything is Ok...But If I want to customize it (Right-Click, Preferences), the following error mesage appears:

An error occurred while loading or saving configuration information for wnck-applet. Some of your configuration settings may not work properly

Details:

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_10/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_10/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_10/prefs/num_rows' stores a non-schema value

I really appreciate the help because this is one of the best function inside Linux (I like )...In advance thanks
Regards

---

### Post by ranf on 2006-01-26
Did you remove the workspace switcher from the bottom panel?

---

### Post by caldico on 2006-01-26
Yes...I changed all my desktop and tried to put the Desktop Switcher again using "Add to Panel"....I got the error messages previously posted....thanks :(

---

### Post by Owdy on 2006-03-22
I have same problem. How do i fix this?

---

### Post by Admiral Valdemar on 2006-03-22
Count me in too. I get the same error (and not just for this applet, for some others too when checking their properties). I can get the desktop switcher on the panel, but it shows only one desktop, making it somewhat useless.

---

### Post by Owdy on 2006-03-22
I installed gnome-desktop, that repaired it.

---

### Post by Admiral Valdemar on 2006-03-22
[QUOTE=Owdy]I installed gnome-desktop, that repaired it.[/QUOTE]

You mean the package "gnome-desktop-environment"? I assume installing that won't bugger up my settings in GNOME now.

---

### Post by Owdy on 2006-03-22
[quote=Admiral Valdemar]You mean the package "gnome-desktop-environment"?[/quote]Yes.

---

### Post by leonbrio on 2006-05-20
omg it worked, thx alot =~ (was sad already)

---

