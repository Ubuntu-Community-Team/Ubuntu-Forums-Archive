---
title: "hide recovery mode and memtest on grub dual boot screen"
date: 2009-05-11
forum: General Help
---

### Post by littlehuynher on 2009-05-11
hello 
i recently downloaded ubuntu 9.04 and it's awesome!
and i was wondering if there is a way to hide the recovery mode and memtest selection on the grub dual boot screen? and just have 2 lines one for ubuntu and one for windows

hope i make sense

---

### Post by cholericfun on 2009-05-11
you can edit these in /boot/grub/menu.lst

(you need root permission to edit this file)
i.e.
```
sudo gedit /boot/grub/menu.lst
```

have a good read through the file - it has instructions as to how to change things...
possibly best to just outcomment the options you dont want

---

### Post by pro003 on 2009-05-11
yes, type in terminal:

```
sudo gedit /boot/grub/menu.lst
```

scroll down to what you actually see in grub and take it off, but be careful...

---

### Post by littlehuynher on 2009-05-11
be careful? what could happen
so with this i can change the name too? instead of ubuntu 9.04 kernel,,..... to something else

---

### Post by danwood76 on 2009-05-11
Yes you can change the name etc.
Just look through it its fairly self explanitary.

Only thing is if you remove the recovery mode and something happens to X you wont be able to recover easily.

---

### Post by drs305 on 2009-05-11
You can use StartUp-Manager to easily make this change. The details are in the linked guide in my signature line or go to the ubuntu documentation wiki:
[_http://help.ubuntu.com/community/StartUpManager_]("http://help.ubuntu.com/community/StartUpManager")

You don't have to edit the system file, let this GUI app do it for you. Once installed, just go to the 'Advanced' tab and deselect those two options.

---

### Post by littlehuynher on 2009-05-11
alright thanks everyone
this is great  stuff :)

---

