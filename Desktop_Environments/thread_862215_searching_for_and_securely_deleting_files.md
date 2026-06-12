---
title: "searching for and securely deleting files"
date: 2008-07-17
forum: Desktop Environments
---

### Post by joec3 on 2008-07-17
what program do i use to search for files and is there a program to securely delete files (ie overwrite several times)

---

### Post by mali2297 on 2008-07-17
> **joec3 said:**
> what program do i use to search for files and is there a program to securely delete files (ie overwrite several times)

If you're comfortable with command line tools, then you can use *locate* or *find* for searching.

*locate* is simple and fast, just type
```

locate filename

```
However, it uses a database which might need to be updated at times (it should do so automatically but I don't know how often). To update the database, type
```

sudo updatedb

```

*find* is more advanced. There is a tutorial here:
[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

If you want a GUI tool, then check out [catfish]("http://software.twotoasts.de/index.php?/pages/catfish_summary.html") (available in the repos).

As far as I know, there is no completely secure way to delete files in the ext3 file system. *shred* is an old unix tool which worked for ext2 and might still be somewhat useful. To overwrite and delete, type
```

shred -u filename

```

---

