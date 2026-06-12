---
title: "Windowless Application"
date: 2007-06-16
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-06-16
Hi there,

Is it possible to launch an application in GNOME without having it appear in the Window List of the (by default) bottom panel?

---

### Post by yabbadabbadont on 2007-06-16
You will probably need to install (and learn how to use) devilspie.  It can do what you want.  I would tell you how to use it, but I don't know myself.  I just know that it can be used to adjust the properties of windows such as wether or not they appear in the tasklist or pager.  You can do a lot more with it too from what I've read.

---

### Post by diafanos on 2007-06-18
Install devilspie (sudo apt-get install devilspie)
Open an editor and write:
 > 
(if
        (contains (application_name) "<application_name>")
        (begin
               (skip_pager)
               (skip_tasklist)
       )
)


where <application_name> is the name of the program you want.
Then save the file in ~/.devilspie folder, with a name with suffix .ds (e.g. myapp.ds)

Then, whenever you run program devilspie and open the specific application, it won't be shown in windows list.

PS. Here is a good wiki for [devilspie]("http://wiki.foosel.net/linux/devilspie")

---

### Post by ShareBuntu on 2007-06-18
Thanks for the replies. I've got the following but it doesn't seem to work:
```
(if
(contains (application_name) "xmms")
(begin
(skip_pager)
(skip_tasklist)
)
)
```

Devilspie however works perfectly since I tested it on another application.

---

### Post by ShareBuntu on 2007-06-18
Just figured it out. Application name is "XMMS" and not "xmms". I used the following to get information about the environment:

> echo '(debug)' > .devilspie/test.ds
devilspie

---

