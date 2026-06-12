---
title: "Help main page blank"
date: 2006-02-16
forum: Desktop Environments
---

### Post by knitwit on 2006-02-16
I seem to have corrupted my GNOME and UBUNTU help files. When I click on the life preserver from either the system menu or the panel icon at the top of the desktop I just get a blank page titled 'Help Topics'.

Does anyone know how to restore them?

---

### Post by mustang on 2006-02-16
From a quick search in synaptic :

```
sudo apt-get install ubuntu-docs 
```
```

sudo apt-get install yelp
```

---

### Post by knitwit on 2006-02-17
I've just tried the above and now I've got the 'About Ubuntu' link but nothing else; the GNOME links are still missing as is the Ubuntu 5.10 users' guide. I'm help-less - help!

---

### Post by kenweill on 2006-02-17
Try uninstalling both ubuntu-docs and yelp.
Then reinstall them both.
Im not sure if Removing Completely is safe, but thats what I did with some other aps. Im just not sure with the help files.

---

### Post by knitwit on 2006-02-17
I uninstalled both then reinstalled them only to be given just the 'About Ubuntu' link and nothing else.

---

### Post by knitwit on 2006-02-17
Quite by chance I noticed that when I run 'sudo nautilus' I get the following message:

```

gavin@ubuntu:~$ sudo nautilus

--- Hash table keys for warning below:
--> file:///usr
--> file:///usr/share/gnome/help/user-guide/C
--> file:///root/.Trash
--> file:///usr/share/gnome
--> file:///usr/share/gnome/help/user-guide
--> file:///usr/share
--> file:///usr/share/gnome/help
--> file:///
--> file:///usr/share/omf
--> file:///usr/share/omf/install-docs-man

(nautilus:9158): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table sti ll has 10 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///usr/share/gnome
--> file:///usr/share
--> file:///usr/share/gnome/help/user-guide/C
--> file:///usr/share/gnome/help/user-guide
--> file:///root/.Trash
--> file:///usr/share/omf/install-docs-man
--> file:///
--> file:///usr/share/omf
--> file:///usr/share/gnome/help
--> file:///usr

(nautilus:9158): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 10 elements at quit time (keys above)

```

Could this explain my missing helpfiles? Sorry - I'm completely new to Linux. And I don't have the system help to help me!

---

