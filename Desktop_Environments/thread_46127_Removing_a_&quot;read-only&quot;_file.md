---
title: "Removing a &quot;read-only&quot; file?"
date: 2005-07-03
forum: Desktop Environments
---

### Post by filemanager on 2005-07-03
I just installed Linux yesterday, and I've figured out how to edit a read only file (sudo gedit), but how do I remove it? I created it in attempt to get my sound card working but it didn't work so now I want to delete it. It says I don't have the permissions though =\

---

### Post by mohaham on 2005-07-03
type this in the terminal:
sudo rm -i filename

---

### Post by filemanager on 2005-07-03
[QUOTE=mohaham]type this in the terminal:
sudo rm -i filename[/QUOTE]
 Ah, great thanks :)

i forgot to put the -i  before the filename, but it looks like the file was removed so I guess it doesn't matter. What is the -i for anyway?

---

### Post by cwaldbieser on 2005-07-03
It stands for "interactive".  It will prompt you before removal.  If you type 

```
$man COMMAND
```
you can get a list of all the options for various commands (substitute "rm" for "COMMAND" in this case, etc.).  The manual pages are somewhat boring reading, but they are good when you need to find out how to tweak the behavior of a command.

---

### Post by mohaham on 2005-07-03
-i just makes the "rm" command much safer to use.
it prompts you before deleting anything..

---

