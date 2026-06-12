---
title: "Problem running libs"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Graduate on 2005-12-07
Hey. First post but I've been frorums for some time. I keep getting these errors and I don't know how to fix them.  I'm running e17 and everything runs smoothly except for these two programs.
I get this:
```
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
and this:
```
evidence: error while loading shared libraries: libpcre.so.3: cannot open shared object file: No such file or directory
```

Thanks in advance.

---

### Post by angkor on 2005-12-07
Well the lib isnt on your system.

apt-cache policy libstdc++5
libstdc++5:
Installed: 1:3.3.6-8ubuntu1
Candidate: 1:3.3.6-8ubuntu1

Try installing the lib using apt / synaptic and try again.

---

### Post by schilcha on 2005-12-07
Hi! This is probably the usual stuff, you've already checked (I don't even have a clue, what e17 is). Anyways:

*) are those libraries installed on your system (on mine, they can be found in /usr/lib) -- if not, install the packages "libpcre3" and "libstdc++5".

*) if you already have them installed, but in a non-standard directory (not /lib or /usr/lib), make sure to tell the system where to find them. I usually set the LD_LIBRARY_PATH in my .bashrc (e.g. export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/home/schilcha/local/lib"). You can also check "man ld.so" for other ways to do it. 

*) finally, check the permission of the libraries. They should be readable for the user launching the process. 

Good Luck!

---

