---
title: "gedit temp files, where to find?"
date: 2009-03-05
forum: Desktop Environments
---

### Post by vizualbod on 2009-03-05
Where does gedit store its temp files?

I opened terminal, typed gedit and started writing a document. When I was ready, I unintentionally closed terminal, this closed gedit and I seem to have lost my work.

It has to be stored in some temp file or folder I guess, but I can not find it.

Please help.

---

### Post by houcem on 2009-03-05
Hello Vizualbod.I think that your file is stored in the working directory the moment you started gedit.If gedit is the firdt typer command so the working directory is you home directory "/home/yourusername".

---

### Post by mcduck on 2009-03-05
Temporary/backup files are stored in the working directory, with a "~" at the end of the file name. these files are treated as hidden so you need to enable showing hidden files before you can see them (Ctrl-h if you use Nautilus).

---

### Post by vizualbod on 2009-03-05
Nope, gotta start over again. I think Ubuntu still has a lot of small things (especially command line related) that allows you to shoot yourself in the foot.

E.g. a few weeks ago I was SSH on the server and I wanted to delete contents of a directory on that machine. I have not noticed the server disconnected me and thew me in my home directory as I was working in another  window. I switched back to terminal and typed "rm -rf ./* and ouuuuuuuuuuch.

---

### Post by vizualbod on 2009-03-05
It was unsaved document.

---

