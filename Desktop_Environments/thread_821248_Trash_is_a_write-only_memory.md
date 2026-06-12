---
title: "Trash is a write-only memory?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by kornelix on 2008-06-07
The Gnome Trash application was overhauled to keep some metadata about trashed files, apparently with the intention of being able to recover files from trash (as in Windows).

I can put files in Trash, I can see what is in Trash, and I can empty Trash, but there is apparently no way to recover single files as you would expect. I can find no menu item about recovering files from trash. Opening a Trash file within Nautilus produces the enlightening message "Could not open the file trash:///home2_.Trash_1000_fotoxx.xtext."

I can get around the problem by going to ~/.local/share/Trash/files and moving the file manually. Of course this gets the metadata out of synch.

Is this application as stupid as it looks, is my system defective, or am I ?

---

### Post by tcommbee on 2008-06-07
I think currently there's no way to recover files with one click (see [this bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=41850")). But opening trash in nautilus and moving a file to some other place works and also doesn't damage the metadata. You could also instead copy the file from ~/.local/share/Trash/files and then delete it in trash.
I'm not sure about the error message you get. Likely, the app which should open the file doesn't support the [trash can protocol]("http://freedesktop.org/wiki/Specifications/trash-spec") yet.

---

### Post by kornelix on 2008-06-08
I wonder why such a non-functional implementation was even done.

---

