---
title: "Hiding Hidden Windows Files"
date: 2006-03-20
forum: Desktop Environments
---

### Post by goober99 on 2006-03-20
I have my Windows NTFS partition mounted in Ubuntu, so I can access files like my MP3s in both OSes without having to have duplicates of them. Windows leaves these nasty little files that are hidden in Windows. Specifically, desktop.ini and Thumbs.db. Is there anyway to have Gnome hide these files also?

---

### Post by professor_chaos on 2006-03-20
No, not that I'm aware of. In Unix/Linux a hidden file is designated by a name starting with a dot. So unless you want to rename the file, I dont know how its possible.

---

### Post by MetalMusicAddict on 2006-03-20
[QUOTE=professor_chaos]No, not that I'm aware of. In Unix/Linux a hidden file is designated by a name starting with a dot. So unless you want to rename the file, I dont know how its possible.[/QUOTE]
This is one thing that I ran into also. Mild annoyance in dealing with multiple OSs. :)

---

### Post by lha on 2006-03-21
[QUOTE=goober99]I have my Windows NTFS partition mounted in Ubuntu, so I can access files like my MP3s in both OSes without having to have duplicates of them. Windows leaves these nasty little files that are hidden in Windows. Specifically, desktop.ini and Thumbs.db. Is there anyway to have Gnome hide these files also?[/QUOTE]

Create a file called '.hidden' (dot hidden) in the directory where you want to hide files and add the names of the files you want to hide to .hidden. For example, make .hidden and add
```
desktop.ini
Thumbs.db
``` in it. Save it and click reload in Nautilus.

---

### Post by Endolith on 2007-08-07
> **lha said:**
> Create a file called '.hidden' (dot hidden) in the directory where you want to hide files and add the names of the files you want to hide to .hidden. For example, make .hidden and add
```
desktop.ini
Thumbs.db
``` in it. Save it and click reload in Nautilus.

But wouldn't that only work for the directory you added it to?  What Nautilus **really** needs is to treat Windows hidden files and Mac OS hidden files the same way it treats Linux hidden files.  By default.

---

### Post by Dusty Wilson on 2007-12-06
Is there a way to make the .hidden file act recursively?  If not, is there another way to hide files based on a filename or regex recursively within Nautilus?

---

### Post by osdesk on 2007-12-06
Thanks lha.  Works for me.

---

### Post by Endolith on 2008-06-22
> **Endolith said:**
> What Nautilus **really** needs is to treat Windows hidden files and Mac OS hidden files the same way it treats Linux hidden files.  By default.

Ubuntu Brainstorm link: [http://brainstorm.ubuntu.com/idea/7833/](http://brainstorm.ubuntu.com/idea/7833/)

---

