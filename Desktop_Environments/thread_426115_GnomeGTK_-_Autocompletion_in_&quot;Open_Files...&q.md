---
title: "Gnome/GTK - Autocompletion in &quot;Open Files...&quot; dialog not working"
date: 2007-04-28
forum: Desktop Environments
---

### Post by jetthe on 2007-04-28
Hi,

after updating to Feisty the other day I noticed that autocompletion stopped working in all GTK/Gnome file opening dialogs. (Before upgrading, I could just start typing the name of file/directory and the first matching name would be selected.)
Have anyone else noticed this and if so, do you have an solution?

Example dialog from gedit attached.


Edit: This is the output gedit gives me, something is clearly wrong with SCIM...

```

$ gedit 
sh: scim-bridge: command not found
Failed to invoking the agent: No such file or directory
Cannot launch the agent
The messenger is now down
An IOException occurred at scim_bridge_client_imcontext_set_cursor_location ()

```


Edit2:  Installing the scim-bridge-agent package fixed all the above problems.

---

