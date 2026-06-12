---
title: "Trouble Installing cairo-dock"
date: 2008-02-09
forum: Desktop Environments
---

### Post by eeefresh on 2008-02-09
I'm trying to install cairo-dock based on[ this]("http://www.valeriovalerio.org/?p=53") tutorial.  However, I am getting this error in terminal:
```
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

```

Any suggestions?

---

### Post by psylonius on 2008-02-10
Just got the same error message and this is how I solved it:
Install Getlibs following instructions on [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")
Open a terminal screen and run: sudo getlibs /usr/bin/cairo-dock c
Then run: sudo apt-get -f install

After that it worked perfectly for me:guitar:

---

### Post by eeefresh on 2008-02-11
Thanks, that worked!

---

