---
title: "creating a list of files"
date: 2006-09-19
forum: Desktop Environments
---

### Post by evillawngnome on 2006-09-19
So, i want to create a list of my albums. They are in .FLAC format. Each album has a FLAC and a CUE file. Heres how i am making my list, right now:

ls *.cue > albums.list

Now, what would be the best way to strip the .cue off the filenames when they go to the list?

---

### Post by aysiu on 2006-09-19
I don't know the best way, but if you open it with OpenOffice Calc as a CSV (yes, I know it's not really comma separated, but do it anyway), you can import the file as delimited by *.* and then copy the left column into a text file.

Alternatively, you could copy the files to a temporary folder, use KRename to remove the .cue extension, and then pop the names into a text file.

There's probably some clever *sed* command that can do this all at once, though.

**Edit**: I'm an idiot. Just open it with Gedit and do a find/replace (Control-H) for .cue and have it be replaced by nothing.

---

### Post by lamego on 2006-09-19
evillawngnome,
use sed, the following sed expressiong with replace ".cue" with "" .
```
ls *.cue" | sed "s/\.cue//g"
```

---

### Post by evillawngnome on 2006-09-26
Thanks lamego, thats exactly what i did. :)

---

