---
title: "How to copy a file into every sub-folder"
date: 2009-06-08
forum: General Help
---

### Post by Hectux on 2009-06-08
Hi,

I have the following folder structure.

1 file called subU in a certain folder.
Besides this file I have several subfolders (numbered from 0 to 150).

Now I want to copy this file in every subfolder.

How can I do this with a terminal command?


Best regards and thanks for your answers.

---

### Post by lloyd_b on 2009-06-08
```
find . -type d -exec cp subU {} \;
``` while in the directory containing the file "subU" should do the trick.

Lloyd B.

---

### Post by stinger30au on 2009-06-08
that is an amazingly simple script

can you explain in plain english how the script works to simpletons like myself.
thanks

---

### Post by wintermute000 on 2009-06-08
find . -type d -exec cp subU {} \;

looks like find every directory (-type d) and pass that onto the command cp. Not sure about the {} \; though, my CLI skills are only basic grepping and the such ;)

---

### Post by unutbu on 2009-06-08
[A gentle introduction to 'find']("http://ubuntuforums.org/showthread.php?t=1128937")

"-type d" means find directories.
"{}" is replaced with the name of the directory found.
"\;" signals the end to the -exec command. In other words,
everything between the "-exec ... \;" is run once for each directory found.

---

### Post by ad_267 on 2009-06-08
The {} is used by the exec option to indicate the path of the directory found. The \; indicates the end of the command to execute.

---

