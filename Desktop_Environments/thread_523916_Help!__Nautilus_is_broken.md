---
title: "Help!  Nautilus is broken"
date: 2007-08-12
forum: Desktop Environments
---

### Post by Cerinthus on 2007-08-12
Here's my problem.  Nautilus won't load any extensions--nautilus-open-terminal or gnome-mount.  It will do it just fine if I sudo it or log in as root, it only fails for the user.

I can make it try and initialize it if I copy the extensions to ~/.nautilus/extensions-1.0 , but it still won't load them--it only reports that it is in the terminal.  If I try to use either extension, it fails. But if they're left in /usr/lib/nautilus/extensions-1.0/ it won't even try and load them unless I'm root.  The failure is accompanied by a nautilus-debug-log.txt file, that only includes repeating SIG 11s--the same thing I get if it's not loaded.

Any help would be hugely appreciated.

---

### Post by dougfractal on 2007-08-12
sudo apt-get install --reinstall nautilus

---

### Post by Cerinthus on 2007-08-12
Heh, if only 't'were that easy.  Thanks for trying though :)

---

### Post by dougfractal on 2007-08-13
can you create a new user and test nautilus from there

---

### Post by ComplexNumber on 2007-08-13
i wonder if /usr/lib/nautilus/extensions-1.0 has had the permissions changed somehow so that non-root users can't read the files. 
try entering the following on the command line:
**sudo chmod -R 644 /usr/lib/nautilus/extensions-1.0/***

that will give the following permissions

-rw-r--r--

---

