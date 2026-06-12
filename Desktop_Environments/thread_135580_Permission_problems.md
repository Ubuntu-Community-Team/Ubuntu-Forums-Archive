---
title: "Permission problems"
date: 2006-02-24
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-02-24
I have a file under /etc which I have to change slightly.

Now, when opening the properties of that file, it says it's not my own, so I can't change the permissions.

That's weird, I got, appearantly all the permissions I can have (according to System => Administration => Users and Groups)

How do I change the permissions?

G

---

### Post by andrewsawyer on 2006-02-24
from terminal, type 'sudo nautilus'.  This will open Nautilus File Manager as root.  You can then do whatever the hell you want in it.  But be careful!!!  And remember to close it afterwards so you don't get it confused with the standard user level nautilus.

---

### Post by lamego on 2006-02-24
For security sake the default is not to have "root" privileges with your user on Ubuntu.
Using nautilis as root is as GabrielWolff already stated dangerous and you should avoid it.
You shouldn't need to change your config files so often, if there is a file you need to change just type:
```
sudo gedit /etc/yourfile
```

---

### Post by Robgould on 2006-02-24
Here is a little article on linux permissions that you may find interesting.  Both of the ways above are good, I jsut thought you might like a little reading.

---

### Post by andrewsawyer on 2006-02-24
I would agree that using 'sudo gedit /etc/foo.conf' would be much safer that using 'sudo nautilus', as it will just open the specified file rather than give you a root file manager.

That should have been my first suggestion, as it's what I usually use.  Sorry!

---

