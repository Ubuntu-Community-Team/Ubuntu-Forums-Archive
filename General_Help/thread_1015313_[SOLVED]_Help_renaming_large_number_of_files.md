---
title: "[SOLVED] Help renaming large number of files"
date: 2008-12-18
forum: General Help
---

### Post by scratman on 2008-12-18
I need to rename over 1500 files.  All I need to do is remove the first 6 characters from each file.  What is the easiest way to do this?

---

### Post by IllegalCharacter on 2008-12-18
Bash to the rescue:
```
for i in $(ls); do mv $i ${i:6}; done
```
Just type that in the command line and it'll strip the first 6 letters off of everything in the folder.

---

### Post by kaibob on 2008-12-18
Another way to do this is:

```
rename -n 's/^.{6}//' *
```

The -n option tells rename to do a dry run and report the files that will be changed. Afterward, if all looks well, you can change -n to -v to actually change the file names.

REFERENCE:
[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by scratman on 2008-12-28
Thanks for the help guys.  A quick chat with a mate in the pub led me to pyRenamer, which is in the Repos.  Worked a treat!

---

### Post by kaibob on 2008-12-30
I tried pyRenamer and found it to be a very nice program. It will do most of what you need, and the GUI is fairly easy to use. I noticed that the version in the repo's is 4.x and that the version on the author's site is 6.x. Fortunately, the current version is available as a deb.

---

