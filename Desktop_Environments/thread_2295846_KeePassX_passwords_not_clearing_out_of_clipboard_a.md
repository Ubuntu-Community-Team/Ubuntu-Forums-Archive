---
title: "KeePassX passwords not clearing out of clipboard automatically KDE"
date: 2015-09-21
forum: Desktop Environments
---

### Post by courtney2 on 2015-09-21
I use KeePassX for my password manager, and I am used to the feature it has that clears the clipboard after x seconds. One thing I've noticed is that KeePassX isn't clearing the passwords like it should, which leads me to believe this is some power held in KDE since so far GNOME and Cinnamon don't have this issue. Has anyone had any experience in this and have a fix for the issue?

I'm using Kubuntu 15.04

---

### Post by bapoumba on 2015-09-22
Anything in the security tab in preferences ?

---

### Post by CantankRus on 2015-09-22
Using ubuntu/unity, keepassx copies passwords to both the 
[LIST]
[*]primary selection (left mouse selection/middle click paste)
[*]clipboard selection (right mouse copy/paste and ctrl+c/ctrl+v)
[/LIST]

keepassx will clear both of these but if you use a clipboard manager, passwords will remain in the clipboard manager's recent list.

---

### Post by mfrade on 2016-07-01
I had the same problem with KeepassX 2.0.2 and kubuntu 14.04 and I solved it by changing the configurations of klipper (my KDE is not in English, so some option names may not be accurate):
go to: klipper settings -> general -> uncheck option "Prevent empty clipboard" -> Ok

And now KeepassX is working as expected :)

---

### Post by courtney2 on 2016-07-03
Hmmm almost mfrade. It clears the Ctrl+V option when I do that, but the password still remains in Klipper. KeePassX 2.02 and Kubuntu 16.04 with plasma 5.6

---

