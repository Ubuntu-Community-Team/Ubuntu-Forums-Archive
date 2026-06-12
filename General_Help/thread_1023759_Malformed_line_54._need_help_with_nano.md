---
title: "Malformed line 54. need help with nano"
date: 2008-12-28
forum: General Help
---

### Post by Infinete on 2008-12-28
I am using Kubunto 8.10 and now have a malformed line 54 in source list /ect/apt/sources.list (dist), the main problem is i do not have gedit installed and it will not let me due to the malfunction, i do have GNU nano 2.0.7 though, any help?

---

### Post by linuxonbute on 2008-12-28
> **Infinete said:**
> I am using Kubunto 8.10 and now have a malformed line 54 in source list /ect/apt/sources.list (dist), the main problem is i do not have gedit installed and it will not let me due to the malfunction, i do have GNU nano 2.0.7 though, any help?
try this:

sudo nano /etc/apt/sources.list

It will ask for your user password and should then open the file for editing.

Go to line 54 and delete it.  <take care to make sure you dont get the wrong line >

then save the file ( CTRL O )
then exit ( CTRL X )

---

### Post by ajcham on 2008-12-28
The standard Kubuntu install should have a few alternative GUI text editors available, if you aren't happy using a command line one. Try:
```
gksu kate /etc/apt/sources.list
```
or
```
gksu kwrite /etc/apt/sources.list
```

The only reason that people tend to suggest gedit is that is the default GUI text editor in a Gnome-based Ubuntu install, and therefore the most commonly available to forummers.
[SIZE="1"](PS: Is 'forummers' a word, or did I just make it up?)[/SIZE]

---

### Post by Zorael on 2008-12-28
Is gksu even included in a standard Kubuntu installation? I know kwrite isn't.
```
kdesudo kate
```

---

### Post by ajcham on 2008-12-28
> **Zorael said:**
> Is gksu even included in a standard Kubuntu installation? I know kwrite isn't.
```
kdesudo kate
```

Oh, thanks, I hadn't realised that gksu was Gnome/GTK+ specific.

---

