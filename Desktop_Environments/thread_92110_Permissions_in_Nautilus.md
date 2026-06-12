---
title: "Permissions in Nautilus"
date: 2005-11-18
forum: Desktop Environments
---

### Post by jrincon87 on 2005-11-18
Hey. When I try to change a folder's permission, Nautilus only allows to change the permission to the folder itself and no more. I mean, in Windows you have an option which allows you to change the folder and its subfolders and files permissions, automatically. Is this can be done in Nautilus? If not, is there another way to do it?
Thanks.

---

### Post by invalid on 2005-11-18
I can not speak for the workings of nautilus, but I can tell you how to do it through a terminal.
```
chmod -R [mode] [folder]
```
This will call the function recursively (-R) on all subfiles and subfolders.

Cheers,
Cb

---

### Post by doclivingston on 2005-11-18
Keep in mind that (in general) you will want the execute bit set on folders, but not on files.

---

### Post by janz84 on 2005-11-18
[quote=invalid]I can not speak for the workings of nautilus, but I can tell you how to do it through a terminal.
```
chmod -R [mode] [folder]
``` This will call the function recursively (-R) on all subfiles and subfolders.

Cheers,
Cb[/quote]

I wish there was a context menu in nautilus for 'open terminal here'

---

### Post by invalid on 2005-11-18
[QUOTE=janz84]I wish there was a context menu in nautilus for 'open terminal here'[/QUOTE]
I do not use nautilus, but I have seen some posts that suggest```
sudo apt-get install nautilus-open-terminal
```which I believe will solve this.

Forgive me if I am mistaken.

Cheers,
Cb

---

