---
title: "terminal question"
date: 2006-03-19
forum: Desktop Environments
---

### Post by yellow beard on 2006-03-19
how to change into a folder with spaces? etc: Documents and Settings? I know in dos it would be Docume~1...

---

### Post by rpaller on 2006-03-20
Wrap the folder name with double quotes (").

e.g. cd ~/"Documents and Settings"

---

### Post by LordBug on 2006-03-20
You can also use a wildcard to do it, providing there's no other directories that end up matching the wildcard :)  Something like cd ~/Documents* would work.

---

### Post by Maelgwyn on 2006-03-20
Or you can type the first few characters and hit "tab" - it'll fill in the rest for you automagically! :D

---

### Post by Sutekh on 2006-03-20
[QUOTE=yellow beard]how to change into a folder with spaces? etc: Documents and Settings? I know in dos it would be Docume~1...[/QUOTE]

You need to "escape" the space by using a forward (or is it backward) slash

```
cd ~/My\ Documents
```
This tells the terminal that the space is not the end of the command.

Remember that Linux is case sensitive too.  

Maelgwyn's suggestion is one of the great featues of typing in Linux.  Auto-completion is *very* useful for typing long name, with spaces and capitals.  It can save time and remove a lot of typing errors.

---

### Post by yellow beard on 2006-03-20
cheers, all methods work great.

---

### Post by rayburn on 2006-03-20
Thanks guys, I didn't realise this was possible until now!

Cheers!

---

