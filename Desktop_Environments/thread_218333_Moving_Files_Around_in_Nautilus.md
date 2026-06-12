---
title: "Moving Files Around in Nautilus"
date: 2006-07-18
forum: Desktop Environments
---

### Post by gurgle on 2006-07-18
This seems pretty difficult to me. There is no move-to option in the right click menu, and there doesnt seem to be any spring loaded folders. Can anyone help me out with this?

Thanks

---

### Post by k420 on 2006-07-18
personally i dont like nautilus either for that reason but i would just suggest cut copy and paste
maybe you would like to try the file manager krusader or konqueror

---

### Post by argotnaut on 2006-07-18
Or drag and drop.

I do like the "move to" option in Konqueror, but I like Nautilus better overall.

---

### Post by gurgle on 2006-07-18
but in order to drag and drop, i need to use the desktop, or open 2 nautilus windows.

---

### Post by Underscore on 2006-07-18
or you could just cut and paste

---

### Post by gurgle on 2006-07-18
not if i want to *move *the files

---

### Post by reclusivemonkey on 2006-07-18
> **gurgle said:**
> not if i want to *move *the files

Try this link

[http://www.ubuntuforums.org/showthread.php?t=101870](http://www.ubuntuforums.org/showthread.php?t=101870)

---

### Post by wachunei on 2006-07-18
Cut & Paste is the same than move...

or you could use the mv command like this

mv ~/Docs/* ~

it will move all the files inside the Docs folder to your home folder

---

### Post by TheMindField on 2006-07-18
Nautilus does not offer this option, unless you were to write a script for it (such as the "root-nautilus here" script).

A script would not be very hard using the terminal "mv" command.

Other than that i would simply suggest using the terminal, and using the "mv" command to move things around.  You'll need to use "sudo" or root to move restricted folders.

For example:

Navigate to folder that holds file.
Command "mv filename folderlocation"

You can also overwrite the current file with this command.

Command "mv filename filetooverwrite"

Use this with caution, however.

---

