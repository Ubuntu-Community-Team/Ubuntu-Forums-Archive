---
title: "Uninstall cube"
date: 2006-03-27
forum: Gaming &amp; Leisure
---

### Post by jethro10 on 2006-03-27
Sorry, this is possibly a bit of a newbiie question but :-

how do I uninstall the game 'Cube' 

I'm totally lost.
I realise that add/remove works for officially installed programs but this was done via a command line as per the Wiki entry.

Ta
Jeff

---

### Post by Jason_25 on 2006-03-27
Check your /usr/local.

---

### Post by jethro10 on 2006-03-27
Yep,
there is a usr/local/games/cube

is it as simple as deleting the folder?
there is nothin else hidden?
If thats good enough, it'll do me...

J

---

### Post by Jason_25 on 2006-03-27
I think that would be it.  To see any other changes it made to your system there might be a log somewhere.  If not, you can open up that install script with a text editor and try to see what changes it made.

---

### Post by Perfect Storm on 2006-03-27
do a 

```
whereis cube
```

also if you're lucky there's an uninstall script or just do it manually.

---

### Post by -Rick- on 2006-03-27
[QUOTE=jethro10]Yep,
there is a usr/local/games/cube

is it as simple as deleting the folder?
there is nothin else hidden?
If thats good enough, it'll do me...

J[/QUOTE]
Yes thats enough, cube keeps it's files in a single directory.

---

