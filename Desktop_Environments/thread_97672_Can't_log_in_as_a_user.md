---
title: "Can't log in as a user"
date: 2005-12-01
forum: Desktop Environments
---

### Post by Dark_Link2135 on 2005-12-01
I'm getting the session lasted less than 10 secs error, and I tried doing everything listed in [http://www.ubuntuforums.org/showthread.php?t=97540&highlight=session+10+seconds](http://www.ubuntuforums.org/showthread.php?t=97540&highlight=session+10+seconds)

but nothing works.   I also don't seem to have a .ICEauthority in my home directory, so I can't just delete that to have it write a new one....any help?

---

### Post by aysiu on 2005-12-01
What do you mean you don't *seem* to have .ICEauthority? Where are you looking? What error do you get?

---

### Post by stevea1210 on 2005-12-01
.ICEauthority is a hidden file (indicated by the . in the front of the file).  to see hidden files type ```
ls -a
``` in a terminal from your home directory.  You should have one.

---

### Post by Dark_Link2135 on 2005-12-02
[QUOTE=stevea1210].ICEauthority is a hidden file (indicated by the . in the front of the file).  to see hidden files type ```
ls -a
``` in a terminal from your home directory.  You should have one.[/QUOTE]

From the GUI i had it display all hidden files, but it wasn't there.  I ended up fixing the problem by logging in as root (again, which I don't plan to do again since I assume this is what screwed it up) and 
```
chown -R darklink2135 /home/darklink2135/*
```

---

