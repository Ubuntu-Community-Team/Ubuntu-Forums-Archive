---
title: "Error updating flashplayer-nonfree"
date: 2006-09-20
forum: Desktop Environments
---

### Post by neok on 2006-09-20
Today I have an update for flashplayer-nonfree, but it fails during its installation.

Some idea?

Thanks!

---

### Post by mssever on 2006-09-20
I'm having the same problem. Here's the output from apt-get:
```
~:$ sudo rapt -i flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
[Exit 100 ]
~:$
```

---

### Post by MaXiMuS-D on 2006-09-20
Same here. The installer just gets stuck.....

Any ways to fix it?

---

### Post by MaXiMuS-D on 2006-09-20
Okay, got it. Just do sudo update-flashplugin. It won't show any progress, just a "downloading....." message and after getting the file it'll say "done".

---

### Post by MaXiMuS-D on 2006-09-20
Umm.....sorry for the 3rd cpnsecutive post, but this doesn't work either. Sorry.........

---

### Post by mssever on 2006-09-20
> **MaXiMuS-D said:**
> Okay, got it. Just do sudo update-flashplugin. It won't show any progress, just a "downloading....." message and after getting the file it'll say "done".

Didn't fix it for me. update-flashplugin didn't report any errors, but running apt-get afterwords produced identical results.

---

### Post by Ramses de Norre on 2006-09-20
Same problem here..

EDIT: a fix is found [here](http://www.ubuntuforums.org/showthread.php?p=1521585#post1521585).

---

