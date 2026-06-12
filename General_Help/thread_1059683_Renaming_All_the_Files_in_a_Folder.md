---
title: "Renaming All the Files in a Folder"
date: 2009-02-04
forum: General Help
---

### Post by eman245 on 2009-02-04
Hello All,

I have a folder with a bunch of torrent files, that are labeled file_name.torrent.imported

I was wondering if there is a way to rename all these files to file_name.torrent

If possible, I want to do this through the shell. I know it can be done, but just dont know how quite yet.

Thanks in advance for the help.

---

### Post by Neural oD on 2009-02-04
have a look at rename - it requires a bit of perl regex - but I'm sure that won't be too hard to search for on the internet

I recommend that u set up a dummy folder with files - to play around with - so as not to potentially harm any important files - that is until you have the correct regex going

---

### Post by Neural oD on 2009-02-04
just had a look at the man pages for rename - that example with removing the .bak - should work for you - just substitute .imported for .bak

---

### Post by mb_webguy on 2009-02-04
You can also install either KRename or GPRename, which are GUI batch file renaming utilities.

---

### Post by KeyserSoze93 on 2009-02-04
Put the following in a file called rename.sh, in your torrent folder.

```
for i in *.torrent.imported; do
newname=$(basename "$i" .imported)
mv "$i" "$newname"
done

```

Then run:
```
bash rename.sh
```

---

