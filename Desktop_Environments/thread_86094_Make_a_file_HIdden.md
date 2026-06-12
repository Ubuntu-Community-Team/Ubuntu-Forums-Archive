---
title: "Make a file HIdden"
date: 2005-11-04
forum: Desktop Environments
---

### Post by fezzik on 2005-11-04
How do i do it or at least put some kind of password protection on it?

Help

---

### Post by johannes on 2005-11-04
To hide it you just need to put a dot . in front of the name: .yourfile.txt, and it won't show up unless you have made nautilus or similar show hidden files (Ctrl+h , or terminal "ls -a).

I don't know about password protection though.

---

### Post by Animuscorbaccio on 2005-11-04
Ok, so i have checked and i dont have it showing my hidden files, yet it is still showing a file that i had hidden nor can i get in to change the name so that it has a dot in front of it.

Thanks

---

### Post by paddyg on 2005-11-04
[QUOTE=fezzik]How do i do it or at least put some kind of password protection on it?

Help[/QUOTE]

as for the pswd, if you chmod your file 600, only the owner can read and write it.
that's good protection, i think.

---

### Post by Animuscorbaccio on 2005-11-04
as for the pswd, if you chmod your file 60

Ok, tell in the easiest and most dumb person way you can to tell me what exactly that means?

---

### Post by Saiboogu on 2005-11-04
To hide, do this.. At the terminal (right click on the background of Nautilus, the file manager & choose "Open in Terminal") and type:

```
mv name_of_not_hidden_file .name_of_hidden_file
```

That will rename the file so its hidden. To protect it so only you (the owner) can read it:

```
chmod 600 .name_of_file_to_protect
```

EDIT: And just for future reference, use the "Support" forum for questions - this forum is just for posting Tips and HowTos (guides to doing things).

---

### Post by Arktis on 2005-11-04
[CENTER][IMG]http://www.grudge-match.com/Images/too_soon.jpg[/IMG]
[SIZE="5"]**I PITTY DA FOO' WHO POST IN THE WRONG FORUM!**[/SIZE][/CENTER]

---

### Post by poofyhairguy on 2005-11-04
Moved to correct forum.

---

### Post by bionnaki on 2005-11-04
[QUOTE=fezzik]How do i do it or at least put some kind of password protection on it?

Help[/QUOTE]

follow the script instructions towards the end
[http://www.ubuntuforums.org/showthread.php?t=85588](http://www.ubuntuforums.org/showthread.php?t=85588)

---

