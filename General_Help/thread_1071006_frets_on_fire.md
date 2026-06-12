---
title: "frets on fire"
date: 2009-02-15
forum: General Help
---

### Post by mikeonthebeach on 2009-02-15
can any1 help me install frets on fire on ubuntu 8.10, i have downloaded the tar.gz file but dont know how to install

---

### Post by punx45 on 2009-02-15
> **mikeonthebeach said:**
> can any1 help me install frets on fire on ubuntu 8.10, i have downloaded the tar.gz file but dont know how to install

unpack the tar and there is probably a README in there.   that should have install instructions.   im assuming in the GUI you can extract a tar by right click or double click.   otherwise on the command line you can 
```

tar xvvzf package.tar.gz

```

---

### Post by Rmantingh on 2009-02-15
Extract the contents of the file and read the file install.txt.
In there it tells you what you need to get this to run.

$ sudo apt-get install python-pygame python-opengl python-numpy
$ cd <folder you unpacked the tar.gz file in>
$ cd src
$ python FretsOnFire.py

You may need to install additional packages to get this to run
but the above worked for me.

Ruud

---

