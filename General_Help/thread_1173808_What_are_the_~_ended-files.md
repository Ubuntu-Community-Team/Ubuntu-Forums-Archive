---
title: "What are the ~ ended-files?"
date: 2009-05-30
forum: General Help
---

### Post by Gucko on 2009-05-30
Hi guys, when I browse a folder using any browsing technique except Nautilus, I see files that are ended with ~. What on earth are these files? I think they are deleted files or something but how can I get rid of them>? Why Ubuntu shows them up even after deleting the original file? When you delete the file, you meant to delete it completely. These files are very messy and confusing. They make locating a file thorugh a file browser really hard.

---

### Post by matthew1471 on 2009-05-30
It's a 'previous version' or 'backup' of an edited file.

If you edit a file in [for example] gedit, it will create a backup of the file first.

It simply adds a ~ to the end of the filename.

In gedit you can turn off this 'backup' facility.

---

### Post by CatKiller on 2009-05-30
In addition to what matthew1471 said (which is correct):

> **Gucko said:**
> They make locating a file thorugh a file browser really hard.

Files that end with a ~ (as well as files that start with a .) are hidden. They don't get in the way, backups are useful, and it's pretty straightforward to turn off the creation of the backups.

---

### Post by lisati on 2009-05-30
The "~" at the end of some file names is equivalent to the MS-DOS/Windows ".bak" extension, i.e. "BAcKup"

---

### Post by kpkeerthi on 2009-05-30
> **Gucko said:**
>  how can I get rid of them>? 

Verify the list with this command:
```

find . -type f -name "*~"

```

And delete them all with this command:
```

find . -type f -name "*~" -exec rm '{}' ';'

```

---

### Post by Gucko on 2009-05-30
The files aren't hidden, I see them. You can try this by opening Firefox and then:
File>Open File

Browse some directories and you can see them!

EDIT: Yes I can't see them in Nautilus, but with a file browser yes I can.

---

### Post by Poyntz on 2009-05-30
Like everyone's stated already, they're backups

If you want to get rid of them, which I usually do
Type:
```
rm *~ 
```
whilst in the directory of the ~ file

You should generally keep a backup of any configuration files, etc, you modify though, just in case you change something that shouldn't have been changed

---

### Post by kpkeerthi on 2009-05-30
> **Gucko said:**
> 
EDIT: Yes I can't see them in Nautilus, but with a file browser yes I can.
You might have turned on "view hidden files" for file browser. Press ctrl + h, while in a File Browser, to toggle the option.

---

