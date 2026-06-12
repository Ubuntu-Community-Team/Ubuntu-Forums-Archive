---
title: "Help with work place switcher"
date: 2006-04-25
forum: Desktop Environments
---

### Post by Danny Boy on 2006-04-25
I've been playing around with my panels, and finally have everything customized the way I want. I tried to re-add the work place switcher to a panel. Now only one work place shows, when I open preferences I get this

```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_11/prefs/display_all_workspaces' stores a non-schema value

```

I am also unable to select "Show all work spaces in X rows"

Any ideas?

Thanks in advance, 
Dan

---

### Post by Ramses de Norre on 2006-04-25
```
gedit ~/.gconf/schemas/apps/workspace_switcher_applet/prefs/%gconf.xml

```
There is an error in the file.. mine looks like this:[PHP]<?xml version="1.0"?>
<gconf>
        <entry name="display_workspace_names" mtime="1143153055" schema="/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names"/>
        <entry name="display_all_workspaces" mtime="1143153055" schema="/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces" type="bool" value="true">
        </entry>
        <entry name="num_rows" mtime="1143153055" schema="/schemas/apps/workspace_switcher_applet/prefs/num_rows"/>
</gconf>
[/PHP]
Hope it helps.

---

### Post by Danny Boy on 2006-04-25
Still the same error. 

Is there anyway I can dump the applet and install it again?

---

### Post by Goonie on 2006-04-25
I am having exactly the same problem. I think this problem started after I meddled around with gdesklets. I tried a desklet called GnomeBar (I think) which is a replacement for the default gnome taskbar. If I run the desklet I can configure workspace switcher without a problem but if I try to configure the workspace switcher on a regular gnome panel I get the same error Danny Boy got. Pasting Ramses' config did not fix my problem.

---

### Post by Danny Boy on 2006-04-25
Goonie, 

  That's exactly what happened! I tried the gnomebar and didn't like it, when I tried to put together a new panel the work place switcher didn't work. 
 
  It really frusterated me, so I did a format and installed dapper. :)

---

### Post by Goonie on 2006-04-26
*sigh*

Unfortunately, upgrading to an unstable release is not an option on my work laptop so I need to get this fixed somehow. I'm going to do some research later tonight and see if I can't find a solution.

Goonie

---

### Post by Danny Boy on 2006-04-26
Sorry I cannot help, I'm pretty much a newbie myself. 

Good Luck! :)

---

### Post by Efwis on 2006-04-26
for both of you, I would recommend usig synaptic and try reinstalling gnome-applets and gnome-applets-data.

---

### Post by Goonie on 2006-04-26
Thx, I'll give that a try when I get off work.

Goonie

---

### Post by Goonie on 2006-04-26
Nope, that didn't work, still the same errors and the option for displaying X workspaces in a row is still grayed out.

*sigh*

Goonie

---

### Post by Goonie on 2006-04-29
Ok here's an update if you guys are still interested. I opened gconf-editor and removed (unset) every key I could find that referenced the workspace-switcher applet and then reinstalled gnome-applets and gnome-applets-data

Not sure which key did the macig trick but who cares as long as it worked hehe.

Goonie

---

### Post by omen101 on 2006-06-09
I had the same problem. I just used gconf-editor to unset all of the keys in:

/schemas/apps/workspace_switcher_applet/prefs

That did the trick.

---

### Post by twistedwrench on 2006-08-23
OK none of that is helping me still the same message... How do I give the entry a value manually?

Thx for any help:confused:

---

### Post by twistedwrench on 2006-09-01
OK 
If someone has a problem like this you bring up gconf-editor in a terminal and go to the place listed in the error message... then you edit the key manually giving it an integer value of "1". That;s it
Kinda like editing the registry in winblows LOL (I'm a newbie)

---

