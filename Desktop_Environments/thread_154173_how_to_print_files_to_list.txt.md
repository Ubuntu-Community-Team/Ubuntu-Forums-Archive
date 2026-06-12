---
title: "how to print files to list.txt"
date: 2006-04-02
forum: Desktop Environments
---

### Post by sal on 2006-04-02
what is the command to list the file names of a directory into a text file? i thought it would be ls filename.txt but that did not work for me.
i'm using kubuntu dapper.
thanks for any help.

---

### Post by rmjokers on 2006-04-02
To put the contents in a text file, you just need to redirect the output of ls.  Something like this should work:

ls directory > filenames.txt

Where > is the redirect command.

---

### Post by sal on 2006-04-02
thank you very much for that info.

---

