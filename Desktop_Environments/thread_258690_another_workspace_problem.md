---
title: "another workspace problem"
date: 2006-09-16
forum: Desktop Environments
---

### Post by shax on 2006-09-16
Hello,

I'm having a problem with my workspace. After searching the forums it seems like others had the same problem, but none of the suggested fixes worked for me. I think it has to do with gdesklets messing something up (I have since uninstalled it). 

In a nutshell, this is what happened: I was fiddling around with my panel, removed my workspaces and then added it again. After adding, I got the following error message after I tried to make 4 workspaces visible (the option for showing more than 1 on x rows was greyed out): 

```
An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_1/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value

```

I killed the gnome panel and re-added the workspaces, and it seemed to fix the problem, except now my workspaces are unresponsive: nothing switches.

In gconf-editor /apps/workspace_switcher_applet/prefs, I got the following error message when I tried to do anything:

```
Type mismatch: Expected `UNKNOWN, 5' got `Boolean' for key /schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces

```
```
Type mismatch: Expected `UNKNOWN, 5' got `Integer' for key /schemas/apps/workspace_switcher_applet/prefs/num_rows
```
```
Type mismatch: Expected `UNKNOWN, 5' got `Boolean' for key /schemas/apps/workspace_switcher_applet/prefs/display_workspace_names
```

Under the key documentation it says "This key has no schema" for display_all_worspaces, num_rows, and display_worspace_names.

This is what my %gonf.xml looks like:

<?xml version="1.0"?>
<gconf>
        <entry name="display_workspace_names" mtime="1158371122" schema="/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names"/>
        <entry name="display_all_workspaces" mtime="1158413457" schema="/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces" type="bool" value="true">
        </entry>
        <entry name="num_rows" mtime="1158411243" schema="/schemas/apps/workspace_switcher_applet/prefs/num_rows" type="int" value="1">
        </entry>
</gconf>

Any suggestions? 

Thanks!

---

### Post by crossedout on 2006-09-16
You are on the right track.  You'll need to use Configuration Editor.
Navigate to apps -> panel -> applets -> applet_3 (this may and probably is different for yours).  You need to find the applet_<number> that has bonobo_iid value = to OAFIID:GNOME_WorkspaceSwitcherApplet.
Once you know which applet that value is under, navigate to prefs, then change the value of num_rows to 1 and make sure display_all_workspaces is checked.

-Xout

---

### Post by shax on 2006-09-17
It worked!

Thank you.

---

