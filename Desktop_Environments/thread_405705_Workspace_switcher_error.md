---
title: "Workspace switcher error"
date: 2007-04-10
forum: Desktop Environments
---

### Post by Buchardt on 2007-04-10
Hey

My workspace switcher is teasing me. I have 3 desktops, but my workspace switcher shows only one. When I open preferences I get the error message

```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_2/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_2/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_2/prefs/num_rows' stores a non-schema value
```


I've been trying to solve it numerous ways, but it wont really work on me. I've also searched this forum for ealier posts, but found none that could help me.

When i open gconf-editor, i can get my workspace switcher to show 3, but if I remove the workspace switcher applet and add it again, it will only show one, and I get the same error message.

I've attached the schema gconf.xml and the other gconf.xml. I have an idea that these have the wrong format/entries. Can some of you post the content of yours? They are placed in:
HOME/.gconf//apps/panel/applets/applet_#/prefs
HOME/.gconf/schemas/apps/workspace_switcher_applet/prefs/

Please ask if you need more info. I'm running Ubuntu 6.10 with latest gnome.

---

### Post by Buchardt on 2007-04-11
I finally got it to work. I don't know what I exactly did, but I essentially deleted my schema gconf.xml file, and rebooted. I think that was what did the trick.

---

### Post by cyberlion on 2007-07-03
A has this problem, but solved!!! :D

I make this:

1) add de workspace switcher to the panel
2) run the gconf-editor (Alt+F2: gconf-editor)
3) find the key app/panel/aplets
4) in the switcher config I deleting the keys.

And the problem dead!

---

### Post by jojmoj on 2008-04-17
reet i sorted this with a little help from the above post so this is SOLVED:

1.) add the workspace switcher to the panel (right click panel > add > scroll to desktop&windows > window switcher

2.) run the gconf editor (alt+F2: gconf-editor)

3.) navigate to the key: app/panel/aplets/

4.) find the entry for your window switcher applet
      the keys for it are display_all_workspaces, display_workspace_names and num_rows (if that helps at all)

5.) once you have the correct entry right click on the key display_all_workspaces

6.) edit key > type:boolen > value >true

7.) save apply watever and exit

done!

:D

---

