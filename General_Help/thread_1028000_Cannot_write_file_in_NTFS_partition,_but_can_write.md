---
title: "Cannot write file in NTFS partition, but can write to others in its same directory."
date: 2009-01-01
forum: General Help
---

### Post by newagelink on 2009-01-01
I'm attempting to write to a file on my Windows partition, which I think is NTFS. I can write to certain files but not others, and there appears to be no difference in the permissions of the files according to "ls -l". As an example, the "books.shtml" file is the only unwriteable file, all in the same folder:
```
-rwxrwxrwx 2 root root  54301 2009-01-01 00:28 booksread.htm
-rwxrwxrwx 2 root root   2542 2007-05-18 11:29 books.shtml
-rwxrwxrwx 2 root root  63782 2009-01-01 23:08 quot.shtml

```

Attempting to write the unwriteable file yields the error: > **File save error**

Could not write file: "(the file's pathname)" I'm using Bluefish to edit these files, but the same error also occurs in Text Editor.

The Synaptic Package Manager already shows installed the latest version of ntfs-config, 0.5.5-0ubuntu1. I ran "sudo ntfs-config" in the Terminal and I already have the "Enable write support for internal device" checkbox checked.

Does this error make sense? Any help would be greatly appreciated.

---

### Post by dcstar on 2009-01-02
> **newagelink said:**
> 
......
Does this error make sense?

Unless you show the exact error, then no.

---

### Post by newagelink on 2009-01-02
[COLOR="Indigo"]I quoted it; what more should I do? Would a screenshot of the text help? (It's the same text I have quoted.)

At the suggestion of wj32 at #ubuntu, 'recreated' the file and that seems to have removed the problem. I moved it to another folder, opened it in Bluefish, and saved it into the original folder.

That seems to have removed this problem, but I don't know what teh problem was![/COLOR]

---

