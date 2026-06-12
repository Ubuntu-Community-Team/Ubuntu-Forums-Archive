---
title: "Gnome Keyboard Shortcuts only offers &quot;Switch to workspace&quot; 1 and 2"
date: 2008-11-12
forum: Desktop Environments
---

### Post by eehouse on 2008-11-12
Just installed Intrepid Ibex.  I've been using Ubuntu since Dapper, and always I've upped the number of workspaces to six and then, in Keyboard Shortcuts, bound "Switch to workspace N" to function key FN for N in 1..6.
But having increased the number of workspaces, and rebooted just to be sure, I'm only offered "actions" "Switch to workspace 1" and "2".  Is this a new bug?  Is there a text config file I can edit to work around it?

---

### Post by bradmont on 2008-12-22
Does anyone have a solution for this?

Edit:  Oh, I just did it in CCSM.

---

### Post by aquameta on 2009-02-19
bump

---

### Post by iSa-111 on 2009-05-25
Run 'gconf-editor'. Edit keys /apps/metacity/global-keybindings/switch_to_workspace_X.

---

