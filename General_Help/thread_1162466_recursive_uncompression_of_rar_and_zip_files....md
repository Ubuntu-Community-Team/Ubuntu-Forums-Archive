---
title: "recursive uncompression of rar and zip files..."
date: 2009-05-17
forum: General Help
---

### Post by juanp.contreras on 2009-05-17
Hi...

I was wondering if somebody could write a script to uncompress some files in a directory structure in a recursive way... something like listing the files by their absolute path in order to uncompress them and delete the compressed sources...

thanks...

---

### Post by jms1989 on 2009-05-17
hmm, nautilus can extract zip files but it requires unrar to extract rar files. file-roller can do the same.

---

### Post by hvbakel on 2009-05-17
The following command will recursively find all *.rar files, starting from the current directory and it will extract them to the current directory:

```
find ./ -name '*.rar' -exec unrar e {} \; 
```

The following command will do the same for zip files:

```
find ./ -name '*.zip' -exec unzip {} \; 
```

you might want to google the find -exec combination, it's very powerful.

---

### Post by mb_webguy on 2009-05-17
If you install the p7zip-rar package, you can use the following command to extract all archives in a directory including its subdirectories:```
find ./ -exec 7z e {} \;
```
This will try to extract *all* files in the current directory and its subdirectories.  If the file isn't an archive, 7z will simply fail and move on to the next one.

---

### Post by juanp.contreras on 2009-05-17
Thanks...! 

I ran those commands at the same time, and, because there were some replicated files, the directory became a mess... but it's ok because I used flint to remove replications and the data is going to be indexed... so there's no problem at all....!

---

