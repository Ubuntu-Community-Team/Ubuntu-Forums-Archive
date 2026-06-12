---
title: "Can I do this on the command line?"
date: 2009-04-18
forum: General Help
---

### Post by sr243 on 2009-04-18
I'm trying to get a certain output format to in a text file.
Specificially, I want to generate a file that has all the filenames in a given subdirectory, but including the name of the subdirectory itself.

e.g. I want something like this in the text file

foldername/file1.bin
foldername/file2.bin
foldername/file3.bin

I am currently using "ls foldername > filelist.txt" and then manually editing filelist.txt, adding "foldername/" in front of each line. Is there a way to do this automatically on the command line (since I need to do this with a folder with 1000s of files)

Thanks.

---

### Post by ostrm on 2009-04-18
If you want to prepend the full directory name, you can use a wildcard, which invokes ls slightly different (the -d option prevents descending in subdirectories)

```

$ ls tempdir
temp1  temp2  temp3

```
as opposed to
```

$ ls -d tempdir/*
tempdir/temp1  tempdir/temp2  tempdir/temp3

```

You can of course also give the full pathname
```

$ ls -d /home/hero/tempdir/*
/home/hero/tempdir/temp1  /home/hero/tempdir/temp2  /home/hero/tempdir/temp3

```

---

### Post by kaibob on 2009-04-18
If I understand correctly, you want the text file to contain files but not directories in the target directory, and you want the files prefixed with their parent directory. If that's the case, you can use the find command. For example, to list files with their parent directory in the /home/kaibob/documents directory, enter the following:

```
cd /home/kaibob

find documents -type f > file.txt
```

---

