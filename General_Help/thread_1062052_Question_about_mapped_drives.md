---
title: "Question about mapped drives"
date: 2009-02-06
forum: General Help
---

### Post by robmypro on 2009-02-06
I am just getting started with Ubuntu (long suffering Win user) and I really like this OS! I do have a question about mapped folders. I have a Win2k3 server I need to access from Ubuntu, so I mapped it. Everything works fine, but I do not seem to be able to access this folder within applications. The file picker does not show the share on the left side. I can see it in the File Browser, but not when trying to open a file, for instance in Evolution (or just about any other program).

Maybe I have not attached this folder correctly. I used the Connect To Server option and created a bookmark. What I really want is to permanently show this folder on every folder/file picker dialog throughout the system.

What is the best way to make a share been seen throughout Ubuntu?

Thanks!

---

### Post by kanikilu on 2009-02-06
Not all program's use the same file browsing dialog boxes. For instance, I use some KDE apps even though I use the default Gnome DE, and their dialog boxes are obviously different and don't show the same things that Gnome apps do.

When you use the Connect To Server option, it creates a mount point at /home/username/.gvfs, look under that directory from programs like Evolution, you should see a sub-directory for each of your "mapped drives".

---

