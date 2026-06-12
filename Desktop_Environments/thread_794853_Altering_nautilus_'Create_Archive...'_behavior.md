---
title: "Altering nautilus 'Create Archive...' behavior"
date: 2008-05-15
forum: Desktop Environments
---

### Post by tweak on 2008-05-15
Since at least Edgy I've been irked with the format options that are available from the "Create Archive..." entry in Nautilus' right click menu.

With a fresh install of Hardy the annoyance has peaked and I'd really like to be able to change the list of archive formats: from '.tar.gz' to '.tgz', from '.tar.bz2' to '.tbz2' etc.

It's a tiny difference, obviously, but one that annoys me no-end, and surely something not too difficult! Is there any way to make these changes without going through some major modification like recompiling nautilus from source?

---

### Post by Awalton on 2008-05-15
Can't change it through Nautilus at all ;), it's a Nautilus-extension that file-roller supplies. And you can't change it there without recompiling the file-roller module from source.

But, OTOH if this is annoying enough for you that you want to change it, the amount of source that you need to change is not that huge: 

[http://svn.gnome.org/viewvc/file-roller/trunk/src/fr-command-tar.c?revision=2226&view=markup](http://svn.gnome.org/viewvc/file-roller/trunk/src/fr-command-tar.c?revision=2226&view=markup)

Everywhere you see e.g. "new_name = g_strconcat (c_tar->uncomp_filename, ".gz", NULL);", you'll need to change the logic to remove the .tar extension and concatenate the "simplified" extension. File-roller internally handles .tgz the same as .tar.gz, so you won't see any other changes in functionality by doing this change.

And who knows, if you do a cleaned up version of the patch with an option to turn it on and off and such, maybe it'll get accepted upstream...

Good luck,
-A.Walton

---

