---
title: "Hide lost+found on extended partition - possible ?"
date: 2009-06-19
forum: General Help
---

### Post by credobyte on 2009-06-19
I was wondering, is it possible to hide ( don't want to remove it .. might be useful in the future ) lost+found folder ? I've an extended partition for music/backups and I want to see it clean, not "full" with some weird folders, not created by me.

Any ideas ?

---

### Post by sdennie on 2009-06-19
You can create a file in the same directory as the lost+found directory called .hidden with the following contents:

```

lost+found

```

That should cause it to be a hidden file in most/all gnome apps.

---

### Post by credobyte on 2009-06-19
> **sdennie said:**
> You can create a file in the same directory as the lost+found directory called .hidden with the following contents:

```

lost+found

```That should cause it to be a hidden file in most/all gnome apps.

And what if I'll need to use *fsck* ? I want to hide it from my eyes, not to rename/remove/replace it.

---

### Post by sdennie on 2009-06-19
> **credobyte said:**
> And what if I'll need to use *fsck* ? I want to hide it from my eyes, not to rename/remove/replace it.

That's exactly what .hidden does.  It just hides it from gui applications.  If you bring up a terminal and cd into that directory, you will still see the file.  If you are in Nautilus or an Open dialog box, you can hit Ctrl-H and see the file too.

---

### Post by credobyte on 2009-06-19
```
.directory != directory
```

Am I wrong ? How it's possible for me to access *lost+found* if it's not there ( *.lost+found* is not the same as *lost+found* ) ?

---

### Post by michy99 on 2009-06-19
You misunderstand. You do not do anything to lost+found. You make a text file named .hidden and in that file you put the name of any file or directory you want to be hidden to gui applications.

---

### Post by credobyte on 2009-06-21
> **michy99 said:**
> You misunderstand. You do not do anything to lost+found. You make a text file named .hidden and in that file you put the name of any file or directory you want to be hidden to gui applications.

Thank you ! .hidden did the job and all ( useless ) folders are hidden now :)

---

