---
title: "File Merger?"
date: 2009-06-01
forum: General Help
---

### Post by Jekshadow on 2009-06-01
I have a collection of text files (some .lst, some .dic) and I was wondering if there was a program/script to merge them all into one (giant) .lst file. They are about 10-20MB each and there are 29 files total. so about 400-500MB total.

---

### Post by Jekshadow on 2009-06-01
BUMP

Help?

---

### Post by mb_webguy on 2009-06-02
Assuming they're all text files (regardless of file extension), then you're looking for the cat (for "con**cat**enate") command.

Assuming the files are all in the current directory, and these files are the only files in the directory, you can simply use the command "cat ./* > *somefile*".  It you want to specify the files (such as if they are in different directories) and the order in which they should be concatenated, just use the command "cat */path/to/file1 /path/to/file2 /path/to/file3 [...]* > *somefile*".

---

### Post by HermanAB on 2009-06-02
Here kitty, here kittycat!
$ cat * > giantfile

---

### Post by lovinglinux on 2009-06-02
You can also sort the merged content like this:

```
cat /path/to/folder/* | sort > newbigfile
```

If you want to sort and remove duplicated lines:

```
cat /path/to/folder/* | sort -u > newbigfile
```

---

