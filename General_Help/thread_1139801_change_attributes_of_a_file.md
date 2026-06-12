---
title: "change attributes of a file"
date: 2009-04-27
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2009-04-27
What is the Linux equivalent of the MSDOS attrib command? I copied some files off a cd and they are read-only. Don't need some of them now but I'm not able to delete them. 'Move to Trash' is greyed out in the menu and in properties I set permissions to read and write. I still can't delete them, I tried to delete them in the terminal, but am denied permission.

I remember a program in OS/2 called BlackHole where you could drag-n-drop anything and it would be gone no matter what. Is there anything like that for Ubuntu?

Thanks

---

### Post by khelben1979 on 2009-04-27
There is two commands which you need here: [chown]("http://en.wikipedia.org/wiki/Chown") and [chmod]("http://en.wikipedia.org/wiki/Chmod").

```
man chown
```
and
```
man chmod
```
for documentation on how to use these commands.

---

### Post by cholericfun on 2009-04-27
i think..
in properties/permissions
you want to change folder access


on the other hand chmod should work fine

in a terminal, go to the folder containing your files and issue ll
before the filename it should give you the current permissions and you'll see if your chmod command worked.

---

