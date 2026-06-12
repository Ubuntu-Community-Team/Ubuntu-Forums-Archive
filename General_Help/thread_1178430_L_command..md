---
title: "L command."
date: 2009-06-04
forum: General Help
---

### Post by PerfectReign on 2009-06-04
Having switched over from openSUSE/KDE to Ubuntu/GNOME, I have been doing pretty well with the new softwere.

One question. I wanted to list details about the contents of a folder in the command line. In openSUSE (bash shell) I'd simply type 'l' to get the directory listing:

kai@linux-ld60:~> l
total 132
drwxr-xr-x 23 kai  users 4096 2009-06-04 10:47 ./
drwxr-xr-x  5 root root  4096 2009-01-05 20:56 ../
-rw-------  1 kai  users  344 2009-06-04 10:47 .bash_history
-rw-r--r--  1 kai  users 1177 2009-01-05 20:56 .bashrc
drwxr-xr-x  2 kai  users 4096 2009-01-05 20:56 bin/
drwxr-xr-x  3 kai  users 4096 2009-06-03 21:14 .config/
drwx------  3 kai  users 4096 2009-01-06 06:01 .dbus/
-rw-------  1 kai  users   25 2009-02-25 19:27 .dmrc


(That's from an openSUSE 11.1 box I run at home to ssh into my home network from work.)

In ubuntu, I don't see this command:

kai@r2d2:~/apps$ l
bash: l: command not found

Is there an equivalent?

---

### Post by unutbu on 2009-06-04
Edit your ~/.bashrc file. Add this:
```

alias l='ls -la'
```

Save, and exit the text editor. Log out, and log back in.
You should now be good to go.

---

### Post by maflynn on 2009-06-04
ls -al should give you what you're looking for.

---

### Post by PerfectReign on 2009-06-04
Ahh, that worked, thank you.

---

