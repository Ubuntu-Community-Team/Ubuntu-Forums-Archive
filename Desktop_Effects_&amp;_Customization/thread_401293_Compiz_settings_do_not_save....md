---
title: "Compiz settings do not save..."
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by Mazza558 on 2007-04-04
I've tried both the Compiz Settings Manager and the Gnome Compiz Preferences applets and changed the settings in them, but the settings don't save, and there's no sign of any changes after closing the window. Funnily enough, if I open the applets again, all the previous settings are present, but they don't seem to have taken effect. What's up?

This is what appears in the terminal when running Gnome Compiz Preferences:

```
** (gnome-compiz-preferences:29667): WARNING **: plugin crashhandler isn't installed

(gnome-compiz-preferences:29667): libgnomevfs-CRITICAL **: gnome_vfs_get_uri_from_local_path: assertion `g_path_is_absolute (local_full_path)' failed

** (gnome-compiz-preferences:29667): WARNING **: plugin animation isn't installed


```

---

### Post by Ateo on 2007-05-10
Hi,

Go into Synaptic and uninstall everything releated to Compiz. This should remove desktop-effects and ubuntu-desktop as well. This is ok. Basically, do a search for 'compiz' and remove it. ALL of it.

Then, after, run this command as your user:```
$ gconftool-2 --recursive-unset /apps/compiz
```

After you do this, reinstalled 'ubuntu-desktop' and 'compiz-extra'.

This should fix you right up.

HTH.

---

