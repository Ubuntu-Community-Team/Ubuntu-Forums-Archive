---
title: "I cannot run any game!"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by danny71 on 2007-05-10
Hello,

I managed to install games designed for Windows with Wine, but I cannot run them because I'm asked to insert original disk, that of course is in the CD drive.

Because of that, I decided to download "no CD" cracks, but I don't know how to copy the files to the destination directory that should be in C:\Program Files in Windows, but Ubuntu doesn't recognize.

Can anybody help me?

---

### Post by loserboy on 2007-05-10
theres a folder in your home directory called  .wine or maybe just wine (without the dot)  in there you should find  C:/program\ files/<nameofprogram>/program.exe

eta: im sure you know already, but just in case you can't see the wine folder go to folder options and view hidden files

---

### Post by DoktorSeven on 2007-05-10
Specificially, it's /home/[your username]/.wine/drive_c

To make it easier to get to, I always make a link from there to a directory in my home directory like so (open terminal and type):

**ln -s ~/.wine/drive_c ~/winedrive**

You can name the second part whatever you want as long as the directory doesn't already exist.

---

