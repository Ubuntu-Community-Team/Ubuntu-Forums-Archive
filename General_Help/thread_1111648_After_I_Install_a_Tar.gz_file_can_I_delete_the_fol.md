---
title: "After I Install a Tar.gz file can I delete the folder?"
date: 2009-03-30
forum: General Help
---

### Post by southzeztpdot on 2009-03-30
I just installed a program that I extracted from a tar.gz file and create the executable with the make. Can I delete the tar.gz folder and remove the executable file I made and will it still work?

---

### Post by spiderbatdad on 2009-03-30
The tar.gz if you like. The folder if you compiled and installed. If you had a folder with a binary you run the program with, then you would not delete that folder. You could make a directory in your home directory called Packages...where you stash this kind of stuff also.

---

### Post by kanikilu on 2009-03-30
You can remove the tar.gz archive. I don't think you can remove the executable that you built...

// Edit -- Too slow, see previous post ;)

---

### Post by southzeztpdot on 2009-03-30
> **spiderbatdad said:**
> The tar.gz if you like. The folder if you compiled and installed. If you had a folder with a binary you run the program with, then you would not delete that folder. You could make a directory in your home directory called Packages...where you stash this kind of stuff also.

The folder that I compiled and installed in is what I'm referring too where the executable file was put. I would like to delete the folder minus the executable file.

---

### Post by xenophed on 2009-03-31
If you installed it and it put it in /usr/(wherever) aka did it have a install script ? did you have to run configure that uses automake and try sudo make install then delete folder.Rename folder (whatever).test or something and try program some have libs and such.:confused:

---

