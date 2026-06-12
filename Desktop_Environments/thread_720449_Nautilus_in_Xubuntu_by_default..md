---
title: "Nautilus in Xubuntu by default."
date: 2008-03-10
forum: Desktop Environments
---

### Post by idrailgag on 2008-03-10
Does anyone know how to make it so that any time I try to open a folder on Xubuntu, it will use Nautilus to browse it?

---

### Post by x1a4 on 2008-03-10
Hi,

Create a script called /usr/local/bin/myfm containing the following:
```

#!/bin/sh
nautilus --no-desktop

```

Do it like so: 

Press Alt+F2 to get the Run dialog and run **gksudo gedit**

This will open a text editor with root priviledges.  Copy and paste the code above into the document and save it as **myfm** (my file manager) in the **/usr/local/bin/** directory.

Set the execute bit for myfm like so: 

Open a terminal and run ```
chmod +x /usr/local/bin/myfm
```



Recreate the symlink /usr/bin/thunar pointing it to /usr/local/bin/myfm

Do it like so: 

In a terminal remove the current symlink: 

```
sudo rm /usr/bin/thunar
```

And replace it like so: 

```
ln -s /usr/local/bin/myfm /usr/bin/thunar
```


To start Thunar after you've made these changes run /usr/bin/Thunar, otherwise Nautilus will be started whenever /usr/bin/thunar is called

---

