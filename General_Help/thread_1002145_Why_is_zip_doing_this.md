---
title: "Why is zip doing this"
date: 2008-12-04
forum: General Help
---

### Post by lsutiger on 2008-12-04
I have a trivial problem that I know how to fix via gui, but want to know how to fix it via CLI.

I have a bunch of files that I want to zip up. I do not want the zip file to save the directory structure. If I am understanding the man page correctly, I need to use the -D option, but that does not work. When I open the zipped file, the directory structure is saved in the file.

What am I missing here?
```
zip -D myfiles.zip /mnt/ftp/eom/<the files>
```

---

### Post by oldos2er on 2008-12-04
So, all the files you want to zip are in a single directory? If that's the case, run "cd /mnt/ftp/eom" first, then "zip -D myfiles.zip *".

 I'm not sure why it's not working for you as you typed it. Seems like it should be.

---

### Post by kaibob on 2008-12-04
The -j option will do what you want. The comments on this option from the man page are:

> Store just the name of a saved file (junk the path), and do not store directory names. By default, zip will  store  the full path (relative to the current path).

---

