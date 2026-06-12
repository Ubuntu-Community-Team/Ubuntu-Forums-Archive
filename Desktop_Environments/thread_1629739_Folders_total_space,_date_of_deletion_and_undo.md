---
title: "Folders total space, date of deletion and undo"
date: 2010-11-24
forum: Desktop Environments
---

### Post by castro1 on 2010-11-24
Three newbie questions I have:    1) How to view how much total space folders take? It doesn't seem to be possible to see that in Nautilus, but I would like to see the space each folder and its subfolders is taking.    2) How to know date I file was deleted? When I open the trash, there is no &quot;date delete&quot; column there.    3) Also: differently from Windows, there is no CTRL+Z to undo deletions, copies and other files operations in Nautilus. Any workarounds?    I appreciate your help.

---

### Post by tom4everitt on 2010-11-24
> **castro1 said:**
> Three newbie questions I have:    1) How to view how much total space folders take? It doesn't seem to be possible to see that in Nautilus, but I would like to see the space each folder and its subfolders is taking.    


Are you familiar with the terminal :) It is a really useful little tool, beloved by pretty much all linux geeks I dare say. Here's a short intro, there's a lot more out there if you google.
[http://www.freesoftwaremagazine.com/articles/command_line_intro](http://www.freesoftwaremagazine.com/articles/command_line_intro) 

From the terminal it is easy to determine the size of a directory with the 'du' command (du for disk usage). You use it like this:

```

du -sh name-of-folder

```
and you get the size of the folder in return. 

Second option, that I know of, is the Disk Usage Analyzer, found in Applications -> Accessories. 

> 
2) How to know date I file was deleted? When I open the trash, there is no &quot;date delete&quot; column there. 
3) Also: differently from Windows, there is no CTRL+Z to undo deletions, copies and other files operations in Nautilus. Any workarounds?    I appreciate your help.

I don't have much useful info on this. Nautilus Elementary could possibly feature some of the things you're looking for. Otherwise you may have better luck with KDE; but KDE is a completely different desktop environment, with all what that means...

---

### Post by castro1 on 2010-11-28
Oh, Disk Usage Analyzer is awesome. Thanks.  I assume, then, that this is not an embedded feature in Nautilus nor any other better Explorer-like program.

---

### Post by tom4everitt on 2010-11-28
I actually just tried Nautilus Elementary (which I think will replace Nautilus eventually), and it actually has that feature (and a lot of other useful improvements, such as Undo, for example). 

Installation instructions here:
[http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html](http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html)

With Nautilus Elementary, just right click on a folder, choose Properties, and it will tell you it's total size.

---

### Post by SecretCode on 2010-11-29
> **castro1 said:**
> Oh, Disk Usage Analyzer is awesome. Thanks.  I assume, then, that this is not an embedded feature in Nautilus nor any other better Explorer-like program.

Disk Usage Analyzer is a separate program, but you can call it from Nautilus if you install nautilus-actions (and configure it via System > Preferences > Nautilus Actions Configuration).

---

