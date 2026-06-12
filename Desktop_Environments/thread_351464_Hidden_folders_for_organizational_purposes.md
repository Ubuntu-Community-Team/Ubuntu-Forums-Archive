---
title: "Hidden folders for organizational purposes"
date: 2007-02-02
forum: Desktop Environments
---

### Post by jbtechie on 2007-02-02
Hi,
I'm wanting to hide folders without changing the path of the said folders.  Are there any file browsers or modifications to current file browsers that have this feature?  

For instance, I would like to hide the 'Desktop' folder that's in my home folder.  I may be able to change the path for that particular folder, and thats fine; but, some applications install folders in my home directory without the period prefix, and I would like to hide these so that my home folder is organized the way I would like it to be.  

If that type of solution isn't available, is there a way to add an arbitrary folder link to the Gnome panel?

---

### Post by empthollow on 2007-02-02
i don't know of any way to hide a folder without using the "." However, you can drag any folder to the panel and when you click on it

---

### Post by aysiu on 2007-02-02
I can't think of an immediate way this can be adapted to your situation, but the principle exists.

For example, in Kubuntu Edgy, there's a file called /etc/kubuntu-default-settings/hidden-root

Any folder in that config file becomes hidden. Unfortunately, it doesn't go more than one folder deep (for example, if you put *home* in that file, /home will be hidden, but if you put *home/username* in, /home/username will not be hidden).

---

