---
title: "Adding a &quot;make symbolic link&quot; to right click in nautilus"
date: 2009-02-04
forum: General Help
---

### Post by Deo Favente on 2009-02-04
Is there any "easy" way of adding a "make symbolic link..." option in the right click menu of nautilus? I don't even know what the heck i mean by easy but if somebody could guide me through the source code a little bit and tell me what kinda things i need to do to do it that'd be great.

---

### Post by amauk on 2009-02-04
It's already there

do you not have a "make link" option when you right click files / folders?

---

### Post by Deo Favente on 2009-02-04
i do but its not exactly what i was looking for. 
What if i wanted to make a symbolic link that goes nowhere? Could be used in my web server (even though this should be in the server configs). Kinda of a dumb reason but this is the most recent reason that happened to me - i wanted to make a visual link in the directory listing to a place that is created by a script and doesnt exsist on the filesystem. I haven't touched the server config file very often and i dont know how to work it.
Also, the "make link" option doesnt work many places - like / or any other place you don't have write permissions. In windoze i like it that you can create a link from that end - and not just the end where the target is located. Also useful if you can't browse to the directory because you don't have the viewing permissions of the parent folders but want to make a link to files contained in the folder or one of the folders themselves in the gui. (i have this config at my network here)
This is a small thing but if you put a bunch of things together i think they can make the OS better. This is not my goal, i just want to do it because it can be done.

---

### Post by fragos on 2009-02-04
You can do anything you want in a nautilus script. Here's a bunch premade [http://gnomefiles.org/download.php?soft_id=2194&where=http%3A%2F%2Fwww.nanolx.org%2Ffree%2FNScripts-3.5.tar.bz2]("http://gnomefiles.org/download.php?soft_id=2194&where=http%3A%2F%2Fwww.nanolx.org%2Ffree%2FNScripts-3.5.tar.bz2"). I use the SendShortctTo one frequently.

---

### Post by Deo Favente on 2009-02-05
This is great! I didn't even know this exsisted! I can easily create a script to do this task using zenity to ask for the link destination. I might post my scirpt  if i get around to it.

---

### Post by jerome1232 on 2009-02-05
You can also do ctrl+shift and drag to create symbolic links.

---

### Post by Deo Favente on 2009-02-05
Here's my script: simple, akward, but works:
```
#!/bin/bash

target=$(zenity --entry --title="Create Link..." --text="Target Path:")
linkname=$(zenity --entry --title="Create Link..." --text="Link Name:")

ln -s -T "$target" "$linkname"
```

i first tried to put it in one line but it looked really dumb

---

### Post by Deo Favente on 2009-02-05
Now, where can i add stuff to the place where it says 'no templates installed' in the 'create document' menu?

---

### Post by fragos on 2009-02-05
Nautilus looks for templates in /home/{user}/Templates. Put any template you want there and Nautilus will offer it as a "Create Document" option.

---

### Post by Deo Favente on 2009-02-06
Thanks. I put a bash script, an html file, and the open office files in there. I think some programs (like Open Office) should put files in there by default.

---

### Post by fragos on 2009-02-06
OpenOffice has it's templates stored eleswhere but that folder is configurable in paths. Gedit also has a plugin for templates which stores them within the configuration data.

---

