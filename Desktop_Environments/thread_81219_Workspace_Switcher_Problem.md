---
title: "Workspace Switcher Problem"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Nomad64 on 2005-10-24
This problem just started happening this morning when I booted up Ubuntu. Being fairly new Linux user, I am kind of stumped on this one. Yesterday, I was playing around with gDesklets, and know that I loaded up LTpager (which probably caused this to begin with).

The workspace switcher on the gnome panel only displays the current workspace, and not all four, thus making it impractical to use. When I try and go into the preferences to change the setting, I get the following error:
[img]http://nomad-clan.com/extra/nomad/error.jpg[/img]

When the "Details" button is clicked, the following output is produced:
```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_9/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_9/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_9/prefs/num_rows' stores a non-schema value

```

From what I can tell, the "schema" file is "/usr/share/gconf/schemas/workspace-switcher.schemas" and that file appears just fine (when compared to a working copy of the file from my server). However, from there, I am at a loss as to where the problem is...maybe some erroneous data in a different file?

Any help would be appriciated.

---

### Post by Nomad64 on 2005-10-26
Ok, since I finally got time earlier today to sit down and look at this problem...I solved it.

From what I can determine, when the LTPager gdesklet is run, it modifies the gconf.xml file that tells the workspace_switcher what to do, basically. This file is located in /home/[username]/.gconf/schemas/apps/workspace_switcher_applet/prefs/ for me, but it may be located somewhere else for other people, I am not sure.

Anyways, when I compared the file in question to a known-good copy of the same file, there were a few small differences. First of all, the XML code itself was written slightly differently (closing of open tags), and there is a "value" attribute added to each of the entry tags. I assue that these "value" attributes is the main cause of the error.

The solution is, obviously, to remove the "value" attributes from the file, or replace the file with a good copy (making a backup of the file, just in case). I have attached one to this post (zipped) for people to use. After the file is edited/overwritten, just remove and re-add back in the workspace switcher applet onto the panel of your choice and then go into Preferences. You should have full control back.

E-mail me if you have any questions.

---

### Post by sumanjay on 2005-11-21
Thanks pal. I encountered the same problem - damn gdesklets :) -  and fixed it using the zipped %gconf.xml file you attached. Thumbs up to you!

---

### Post by sumanjay on 2005-11-21
[QUOTE=sumanjay]Thanks pal. I encountered the same problem - damn gdesklets :) -  and fixed it using the zipped %gconf.xml file you attached. Thumbs up to you![/QUOTE]

Oops! Msged to soon. The problem came right back. I don't have any pesky gdesklets running, but the file is still getting over-written :???:

---

