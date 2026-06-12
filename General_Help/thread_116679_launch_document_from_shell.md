---
title: "launch document from shell?"
date: 2006-01-13
forum: General Help
---

### Post by mvaniersel on 2006-01-13
On windows XP, there is the "start" command that opens a file with the associated application from the shell. e.g. 

start readme.txt -> open readme.txt in notepad
start word.doc -> open doc in word
start image.jpg -> open image browser
start . -> open current directory in windows explorer

Is there an equivalent for the terminal in ubuntu?

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=mvaniersel]On windows XP, there is the "start" command that opens a file with the associated application from the shell. e.g. 

start readme.txt -> open readme.txt in notepad
start word.doc -> open doc in word
start image.jpg -> open image browser
start . -> open current directory in windows explorer

Is there an equivalent for the terminal in ubuntu?[/QUOTE]
I have not been able to find such a feature.. but ofcourse you may doubleclick on a file/directory in the file browser (GUI).

You may ofcourse use for example:
```

gedit readme.txt -> launches readme.txt in gedit.

```

---

### Post by hillbilly on 2006-01-13
Hmm... I dont know whether linux has got something like that. 
But then you could write a shell script which, depending on the extension of the file you have named would open it in the appropriate application.

---

### Post by Gustav on 2006-01-13
open with gnome-open and it uses the standard program to open the file.

---

### Post by mvaniersel on 2006-01-13
Thanks, gnome-open is exactly what I was looking for. :D

---

### Post by DirtDawg on 2006-01-13
Cool, I've been wondering about that too. Thanks.

---

