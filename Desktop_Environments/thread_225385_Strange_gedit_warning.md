---
title: "Strange gedit warning"
date: 2006-07-29
forum: Desktop Environments
---

### Post by conexion200 on 2006-07-29
Hello!
When I run gedit from terminal using su, terminal shows:
```
(gedit:2942): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

What kind of error is it? How to "kill" that?

---

### Post by jordilin on 2006-07-29
what do you type su gedit or sudo gedit? You should type
```
sudo gedit
```

---

### Post by conexion200 on 2006-07-29
With sudo everything is ok. But what's wrong with su?

---

### Post by Malac on 2006-07-29
Apparently this is a bug and has already been reported.

---

### Post by ajgreeny on 2006-07-29
Just out of interest try *gksudo gedit* and see if it still gives the error message:  you should really always use *gksudo* in gnome and *kdesu* in KDE for their respective graphical programs.  You should only use sudo for root actions in non graphical utilities such as *apt-get* or *dpkg-reconfigure*.  I don't know if it will help at all but worth trying.

---

### Post by ardchoille on 2006-07-29
> **jordilin said:**
> what do you type su gedit or sudo gedit? You should type
```
sudo gedit
```

It's not good to use sudo with graphical apps. Sudo should be used at command line for command line apps only. For graphical apps, it's best to use gksudo: [http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by orb9220 on 2006-07-30
I just tried gksudo and get 

orb@Two-Rivers:~$ gksudo gedit /etc/fstab
(gedit:20818): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Malac on 2006-07-30
Re-read my post above.
Honest :)

---

