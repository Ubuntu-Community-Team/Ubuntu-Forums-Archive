---
title: "Nautilus: How can i set a custom icon for a certain file type?"
date: 2009-12-22
forum: Desktop Environments
---

### Post by schmendrick on 2009-12-22
Hello guys!

I am using QT-Creator a lot. 
In nautilus if i double click a QT-Creator project file (they are always named (*.creator) , it opens up qt creator. 

but what nautilus does NOT do is to let me define a default icon for all *.creator files. if in nautilus i right-click a file and go go properties, on clicking the icon i can change the icon FOR THAT PARTICULAR FILE. 

but i dont find an option how i can set up that ALL files of a certain type (meaning files that have a certain extension. the MIME type wont help i guess) will have that type.

can anybody give me a hint how to set this up?
or is there no way to do this in nautilus?

btw: i am using ubuntu jaunty

---

### Post by schmendrick on 2010-01-07
*bump*

ummmh, anyone?

---

### Post by mister_playboy on 2010-01-07
I found a GUI program to do this:

```
sudo apt-get install assogiate
```

You can find it as Applications > System Tools > File Types Editor after installation.

Filetypes such as .tar and .bz2 are listed under "Multipurpose Files" and are found as "x-tar", "x-bzip2", etc.

Right click and pick "Edit", then choose a default icon. :)

---

### Post by schmendrick on 2010-01-07
many thanks!

that works like charm!

---

