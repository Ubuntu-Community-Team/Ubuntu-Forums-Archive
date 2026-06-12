---
title: "What commands do keybindings in GNOME run, if any?"
date: 2018-04-25
forum: Desktop Environments
---

### Post by jonathan90 on 2018-04-25
[COLOR=#111111][FONT=Ubuntu]How do I figure out what command keybindings execute? When we add a custom shortcut, it asks us for a command that the shortcut should run. Naturally, it seems that the default shortcut should also run some command. For instance, "org.gnome.settings-daemon.plugins.media-keys play" let's you add a shortcut for it, but it doesn't say what it does in the system. I would assume that the configuration for that is stored somewhere in the file system, but I can't seem to figure out where. I can change it from it's default value, XF86AudioPlay, to any other shortcut and it still works, so it seems like the actual action doesn't depend on the XF86AudioPlay key.[/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-25
the media keys as well as other stock are built in.

for apps i usually go to /usr/share/applications, then i right click the app->properties & it shows the command.
[ATTACH=CONFIG]279444[/ATTACH]

---

### Post by jonathan90 on 2018-04-25
What do you mean by built in? I can simulate audio play/pause with 'xdotool --key XF86AudioPlay,' and 'XF86AudioPlay' is the default value for the Audio Play keybinding, but I can set it to something else so that the multimedia play/pause key doesn't do anything.

---

### Post by kerry_s on 2018-04-25
> What do you mean by built in?

as in created with the program.

yes, xdotool is a program to simulate keyboard strokes.
yes, you can rebind keys

your confusing. in plain words **what do you want?**

---

### Post by Skaperen on 2018-04-25
i think OP wants to make shortcut keys to things he does not know a filesystem path for, but does know a resource name for, such as "[COLOR=#111111][FONT=Ubuntu]_org.gnome.settings-daemon.plugins.media-keys play_" (i'm not sure if there needs to be a space in there or not).[/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-25
so icons for keyboard shortcuts?

---

