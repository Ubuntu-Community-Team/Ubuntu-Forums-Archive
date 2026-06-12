---
title: "How do I list multiple directories and save to file?"
date: 2009-04-23
forum: General Help
---

### Post by Donalb on 2009-04-23
Hey all, I seem to recall figuring out how to do this before but have forgotten, because I'm an idiot.

I have a directory with say 200 folders. Many of these have subfolders, many have files. 

how do I gather the 1st list plus the 2nd level list. But I don't want further levels, 2 only.

ls -R will do everything, i.e. too much.

Cheers for help.

---

### Post by Onesimus on 2009-04-23
You could try 

ls * > filename.txt

The '>' sends output to the filename.

---

### Post by kanikilu on 2009-04-23
I think you can use the *-maxdepth* option of **find** and then redirect the results to a file with **> output.txt**.

---

### Post by dark_phantom on 2009-04-23
Nevermind, I was thinking of something else.

---

