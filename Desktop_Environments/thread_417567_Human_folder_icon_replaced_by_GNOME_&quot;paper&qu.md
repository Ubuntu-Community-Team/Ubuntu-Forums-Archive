---
title: "Human folder icon replaced by GNOME &quot;paper&quot;"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Steven_B on 2007-04-21
Ever since I upgraded to feisty a month ago, my Human "folder" icons have reverted to the default GNOME "paper" icon.  A screenshot is attached, showing a Nautilus window with the ugly folders.  It only effects the folder icons.  SMB shares, etc, are fine.  Tango and Tangerine also seem to be affected.
I've tried re-installing the human-icon-theme package, without any effect.
Any ideas?

---

### Post by LMP900 on 2007-04-21
At the terminal:

```
gksudo nautilus
```

Then go to the directory where icon files are stored and check if the folder icons are fine there. It might have something to do with permissions.

---

### Post by Steven_B on 2007-04-22
In the /usr/share/icons/Human directory, I found several folder icons:
/48x48/places/folder.png
/24x24/places/folder.png
/scalable/places/folder.svg

The Tango icons also appear to be there.
All the permissions I checked were 644 (Read permission for all users).

---

### Post by Steven_B on 2007-05-10
I upgraded my dapper partition to Edgy, and got the same problem...
Has anyone else had this problem?

---

### Post by heldal on 2007-05-13
I've seen problems related to how the icon-cache is generated if there are files left over from old/conflicting icon-sets (In my case a custom version of the Tango icon-set). Try to re-create the cache for the affected icon-sets:

```

gksu gtk-update-icon-cache -f /usr/share/icons/Tango
gksu gtk-update-icon-cache -f /usr/share/icons/Tangerine
gksu gtk-update-icon-cache -f /usr/share/icons/Human

```

If that doesn't help try:
[LIST=1]
[*]Use synaptic and mark the packages related to human and tangerine icons for complete removal.
[*]Verify that the associated directories in /usr/share/icons are removed. If not - remove them and their contents
[*]Re-install the icon-packages. You might also want to re-install the ubuntu-desktop package at this point as it would have been removed with the icon-sets due to dependences.
[*]Re-create the cache in  /usr/share/icons/Human as described above
[/LIST]

---

### Post by Steven_B on 2007-05-14
That did the trick.  Thanks!
I had installed an older version of Tango manually, so maybe that was the problem.

---

