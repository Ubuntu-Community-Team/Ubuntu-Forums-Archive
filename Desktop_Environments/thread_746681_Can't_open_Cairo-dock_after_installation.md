---
title: "Can't open Cairo-dock after installation"
date: 2008-04-05
forum: Desktop Environments
---

### Post by FS92 on 2008-04-05
As the title says, i can't launch Cairo-dock after the installation. I've tried to remove it and reinstall it, but it makes no difference. I'm running Ubuntu and Compiz Fusion.
I've tried googling it, but i couldn't find nothing...
Thanks for all help:D

---

### Post by F35Blackbird on 2008-04-05
Press Alt-F2, this will launch the application-launcher. Type cairo-dock in application launcher and you should be good to go.

---

### Post by FS92 on 2008-04-06
Thank's for answering

When i try launching with alt+f2 nothing happens, just like when i dobble click the icon:S

---

### Post by overdrank on 2008-04-06
> **FS92 said:**
> Thank's for answering

When i try launching with alt+f2 nothing happens, just like when i dobble click the icon:S

Hi and can you post the output when opening in the terminal? cairo-dock

---

### Post by FS92 on 2008-04-06
> **overdrank said:**
> Hi and can you post the output when opening in the terminal? cairo-dock

Like this?
erlend@erlend-laptop:~$ Cairo-dock
bash: Cairo-dock: command not found

---

### Post by overdrank on 2008-04-06
> **FS92 said:**
> Like this?
erlend@erlend-laptop:~$ Cairo-dock
bash: Cairo-dock: command not found

Hi and yes but the command is case sensitive. cairo-dock

---

### Post by FS92 on 2008-04-06
Ahh! *Hit's his head in the wall*
"
erlend@erlend-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
"

---

### Post by overdrank on 2008-04-06
> **FS92 said:**
> Ahh! *Hit's his head in the wall*
"
erlend@erlend-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
"

Hi and I had a similar issue the other day, did you install via a tar or a deb file.
[https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108](https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108)
I finally installed with the top deb file.

---

### Post by FS92 on 2008-04-06
I did install it with the .deb file you linked to.
Anyone know what i should do? It's obvious it can't find the lib-glitz directory...?

---

### Post by FS92 on 2008-04-07
Anyone know what to do?
I'm missing Cairo-dock:rolleyes:

---

### Post by FS92 on 2008-04-08
*Bump*

---

### Post by FS92 on 2008-04-10
Nobody knows?
Hmm... Any other good docks for ubuntu i can you then?
I loved Cairo-dock, but it's obvious it wont work >.<

---

