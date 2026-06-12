---
title: "Help! (thats not a beatles song)"
date: 2009-06-15
forum: General Help
---

### Post by t4ggs on 2009-06-15
I want to get rid of windows and copy all my files to an ext3 partition, the problem is that many of my filenames are not compatible with linux, for example having to files in the same folder in windows, called A.txt and a.txt..how would linux recognize it? or a file called "document, very important.txt" do u see the problem?? or -doc.txt

i dont want to copy one file at a time just to be sure that all my data is still there

so what im looking for is a windows program that can inspect all my directories and files and check for names that are not compatible with linux, and let me know about this files


anybody knows such a thing??? thanks

---

### Post by lloyd_b on 2009-06-15
I really don't see what the problem is.  The ext3 file system can handle pretty much any name that windows can, seeing "A.txt" and "a.txt" as two different files, having spaces in filenames, filenames that start with "-", etc.

About the only thing you can't do with a ext3 filename is have a slash character in it.

Lloyd B.

---

### Post by rizman on 2009-06-15
I'm no expert, but as far as I see it, ext3 is less picky regarding file names then FAT or NTFS.

For example, under NTFS you cannot have A.txt and a.txt in the same directory because it is not case-sensitive whereas ext3 is. Hence, A.txt and a.txt can co-exist in the same directory as 2 different files without problems.

---

### Post by t4ggs on 2009-06-15
ok, maybe i didnt gave the best examples, but i do have files that there names cannot be seen in linux, i know that cause when mounting my ntfs partition in linux, there are some files that are not showed...i dont remember wich one exactly, i think those with a comma or something else, dont know...anyway is there any way to check my windows files in order to know if they will be all readible in linux?

---

### Post by t4ggs on 2009-06-16
anyone?

---

