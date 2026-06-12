---
title: "Edgy - Bug with Home Folder launcher on Panel"
date: 2006-11-02
forum: Desktop Environments
---

### Post by sizzam on 2006-11-02
Can anyone else replicate this problem?

Click on 'Places', click your mouse down on 'Home Folder' for a second, then drag it to your desktop to create a shortcut to 'Home Folder' on your desktop.  Drag that shortcut to your top panel to make a launcher on your panel for 'Home Folder'.  So far, so good.

Next, reboot your system.   When you log back in, your launcher for Home Folder that you had put on your top panel will be gone.  If you had it surrounded by other launchers, you will see an empty placeholder  where it was before.

Now, drag the shortcut from your desktop back up to your panel again.   You now have a new launcher for 'Home Folder' on your top panel AND your old one reappears as well.

Very strange...

---

### Post by Natronomonas on 2006-11-12
I have the same thing, although I don't have to reboot - merely move the launcher. Same with custom-made launchers...
Didn't have this with 6.06, unless I'm suddenly doing something wrong (not entirely outside the realms of possibility : )

---

### Post by Natronomonas on 2006-11-12
I've found that reboots etc don't make the home folder launcher disappear, even when created as described earlier.
However, other launcher icons seem to lose all detail (icon, command, comment etc) whenever I try to move them (when locked/unlocked).

---

### Post by terces on 2006-11-21
I'm having the exact same problem with the launcher information disappearing when I move the icon within the launcher.  

I just did a fresh install of 6.10; I didn't have this problem with 6.06.

---

### Post by sscotti on 2006-11-24
I'm having the same issue.  I upgraded over the internet using the Update Manager and when I rebooted I had problem created custom launchers on my panel.  They would create fine and the icon would be correct, but if I dragged the icon to a different position on the panel it would revert to an undefined icon and the launch information is erased.

Is this an recognized bug and has it been reported.  Is there an alternative launcher to use for Gnome?

---

### Post by sscotti on 2006-11-27
There is apparently a bug report already filed for this:

[http://bugzilla.gnome.org/show_bug.cgi?id=355513](http://bugzilla.gnome.org/show_bug.cgi?id=355513)

There is a patch there also, although it isn't final apparently.

The patch is here:

--- gnome-panel-2.16.1/gnome-panel/launcher.c.launcher-copy	2006-11-14 17:20:12.000000000 -0500
+++ gnome-panel-2.16.1/gnome-panel/launcher.c	2006-11-14 17:20:46.000000000 -0500
@@ -1048,12 +1048,20 @@
 	GnomeVFSURI *dest_uri;
 	char        *new_location;
 	const char  *filename;
+	char        *path;
 
 	new_location = panel_make_unique_uri (NULL, ".desktop");
 	
+	if (!g_path_is_absolute (location))
+	  path = panel_make_full_path (NULL, location);
+	else
+	  path = g_strdup (location);
+
 	source_uri = gnome_vfs_uri_new (path);
 	dest_uri   = gnome_vfs_uri_new (new_location);
 
+	g_free (path);
+
 	gnome_vfs_xfer_uri (source_uri,
 			    dest_uri,
 			    GNOME_VFS_XFER_FOLLOW_LINKS,

including the typo fix.

How does one apply the patch??

---

### Post by terces on 2006-11-28
I was reading through the bug report and a reporter said that the middle-mouse-button can be used to successfully drag the icon and I can confirm that it does work.  

If you wanted to patch the file, I'm guessing you'd put the info in a .patch file and switch to the directory that contains the file that needs to be patched and run something like

```
patch -p0 < patch-file-name-here
```

I lived with moving the launchers to where I wanted them and then put in the information, but now with the middle-click drag I don't see too much of a reason to apply a non-final patch.  I'm sure it'll update sometime through Synaptic.

---

