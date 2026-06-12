---
title: "Is it possible to combine clamscan --exclude"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Gotou on 2006-10-07
Hi!  I'm trying to speed up clamscan by listing the file types or file extensions to ignore, ie: *.txt, *.jpg, *.gif, *.ttf, *.pfm, *.pfb, *.cdr, *.ai, etc.

The man pages says --exlcude=PATT.  Ok, so do I list each file type in a long line like the above ie example or do I have to put "--exclude=" in front of each and every one?

Is there a config file for clamscan where I can list all the files and directories to ignore?

Thanks!

---

### Post by timetunnel on 2006-10-07
--exclude needs a *regular expression* as an argument. That's different from filename matching with wildcards like *.jpg. Example:  
```
--exclude=".jpg$|.txt$|.gif$"
```
This would exclude all files *ending* with .jpg .txt or .gif

You seperate each pattern that you want to match with a pipe | and enter the search expression. Since you want the *file extension* as a search pattern, you have to make sure that only the *end* of the filename is looked at. That's done with the dollar sign $ at the end of each search expression. If you omit the $, files like "my.jpg.old" would be excluded as well.

There are also some programs in the repositories that help you understand how regular expressions work: "kodos" and "kiki".

---

### Post by Gotou on 2006-10-07
Thanks timetunnel!  I like the way you explained the command by breaking it down.  Better than a man page!

---

