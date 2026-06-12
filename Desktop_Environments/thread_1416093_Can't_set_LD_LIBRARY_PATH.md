---
title: "Can't set LD_LIBRARY_PATH"
date: 2010-02-25
forum: Desktop Environments
---

### Post by fabiomarques on 2010-02-25
Hi, i''m using an java api who needs to acces native libraries of an installed version of ffmpeg.
this api uses some enviroment variables, when i try to set the LD_LIBRARY_PATH, the modification don't work, i tried to set at de .bashrc script file, but the "export" just work at command line, don't work to my browser. Then i tried the .profile script file, but the LD_LIBRARY_PATH still the same and don't work.
Finally i tried to sue the "/etc/ld.so.conf", i put th edirectory there and execute ldconfig, but don't work too.
I would like to know if i'am doing something wrong or if this is an bug.
I tried with Ubuntu 9.04 an 9.10.
Thanks!

---

### Post by spiderbatdad on 2010-02-25
can we see the command you used in .bashrc?
Wondering if you need export $PATH as well as export LD_LIBRARY_PATH

---

### Post by fabiomarques on 2010-02-26
export XUGGLE_HOME=/usr/local/xuggler
export LD_LIBRARY_PATH=$XUGGLE_HOME/lib:$LD_LIBRARY_PATH
export PATH=$XUGGLE_HOME/bin:$PATH

I used this 3 commands.
only works in .bashrc, but the problem is this variables has limited scope, i need there visible for all applications.

---

### Post by spiderbatdad on 2010-02-26
not sure but i think the problem is in the first line...export XUGGLE_HOME=/usr/local/xuggler
where /usr/local is not necessarily in $PATH, however, export XUGGLE_HOME=/usr/local/**bin**
might work.

And also, possibly:
export XUGGLE_HOME=/usr/local/bin
export LD_LIBRARY_PATH=$HOME/XUGGLE_HOME/lib:$LD_LIBRARY_PATH
export PATH=$HOME/XUGGLE_HOME/bin:$PATH

---

### Post by fabiomarques on 2010-02-27
No the first line is correct!
xuggle is the api who i need to load in runtime!
all librarie is in the directorio "/usr/local/xuggle/lib", i need this path setted at the LD_LIBRARY_PATH!

---

