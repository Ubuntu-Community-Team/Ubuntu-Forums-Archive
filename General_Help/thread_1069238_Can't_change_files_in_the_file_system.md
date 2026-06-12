---
title: "Can't change files in the file system"
date: 2009-02-13
forum: General Help
---

### Post by michael1384 on 2009-02-13
I'm trying to put a mod folder in the game 'Frets on fire' and I get this:

```
Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///usr/share/games/fretsonfire/data/mods"

```

What can I do? All permissions are allowed for my account.

---

### Post by mb_webguy on 2009-02-13
You're sure you have read permissions on the archive, and write permission for the directory in which you're trying to extract it?

Try extracting it using "sudo".

---

### Post by michael1384 on 2009-02-13
How exactly do I check, or use the terminal to extract fo that matter?

---

### Post by mb_webguy on 2009-02-13
> **michael1384 said:**
> How exactly do I check, or use the terminal to extract fo that matter?

In the terminal, use the command "ls -la /path/to/dir" (or just "ls -ls" for the current directory) to show you a fill listing of all of the files and folders in a directory and their permissions.  The first column, which is a series of 10 characters, shows the file permissions.  The first character indicates whether the item is a directory ("d") a link ("l") or a normal file ("-").  The next three characters are the read, write, and execute permissions for the owner of the file or directory.  The next three characters are the permissions for the group associated with the file or directory, and the last three are the permissions for everyone else.

The current directory is listed at the top as ".".  In order to extract files to this directory, you need to have write permissions for the directory.  To extract an archive, you must have read permission for the archive, and write permission for the directory where you want to extract it.  For most system directories, only root (the owner of these directories) has write permission.

To use the Archive Manager as root, you can type the command "gksu file-roller".

---

### Post by michael1384 on 2009-02-13
Thanks!

Using the file manager as root worked.

---

