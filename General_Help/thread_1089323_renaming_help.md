---
title: "renaming help"
date: 2009-03-07
forum: General Help
---

### Post by tjtoml on 2009-03-07
I have 100+ files that are named in the same format, which is a string of numbers, followed by an underscore, followed by the filename. (1234_file_name.filetype) I would like to remove the numbers and underscore from the front of the files. Does anyone know how to do this?

---

### Post by s.dalas on 2009-03-07
> **tjtoml said:**
> I have 100+ files that are named in the same format, which is a string of numbers, followed by an underscore, followed by the filename. (1234_file_name.filetype) I would like to remove the numbers and underscore from the front of the files. Does anyone know how to do this?

Did you try mouse right clicking and then rename?

---

### Post by justborn on 2009-03-07
do u mean that u wanna do it for all the file at once ,using some single command?

---

### Post by x33a on 2009-03-07
install krename. really good gui based mass-renamer.

you can search for a pattern and replace it with anything.

---

### Post by lovinglinux on 2009-03-07
pyRenamer is excellent for batch renaming files.

---

### Post by tjtoml on 2009-03-07
had success with pyrename. Didn't do exactly what I wanted but it made it a 5 minute process instead of a five hour one. Thanks!

---

### Post by geirha on 2009-03-07
If you don't mind the terminal, the rename command is very handy.
```
rename -v 's/^\d+_//' *.filetype
```

---

### Post by tjtoml on 2009-03-08
i actually love the command line, i just didn't know there was a rename command, ha.

---

