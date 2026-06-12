---
title: "apt get install problem"
date: 2005-11-15
forum: Desktop Environments
---

### Post by hollowhead on 2005-11-15
I posted yesterday on this issue.  I tried fiddling with the sources file but since I do not have internet access yet that made matters worse.  I tried installing using dpkg but both fvwm2 and xmms gave multiple dependancy errors.  Fvwm had more but they overlapped and could be summed up as not being able to to find various library files such as gtk and tk libs which I know at least some of which are there.  Both are recent downloads and since my breezy badger is pretty up to date this cannot actually be the problem can it?  It must be path problem??!!??  Can anyone help.  I undid the dependency problem by use of synaptic and editing the sources file so I could run apt-get w/o error again.  

Not being able to install debs made me decide to make sure I had gcc.  This is another puzzle.  Typing gcc -v gave a "command not found".  Searching for gcc through up files dirs and library gallore.  I seem to have versio 4.02.  Again this must be path thing although I've not encountered this on other distros were gcc would run from any dir.  A bit worried I will not be able to install modem drivers or anything else by any means.  PS all above tried from /home and /root dirs.

---

### Post by DJ_Max on 2005-11-15
GCC is not installed by default. You need the package *build-essential* (Note: this is a meta-package which just depends on various other files.) fvwm2 and xmms require quite a few libraries in the repository. You need to install them. (when it says GTK and TK libraries, there are serveral available, most which are not installed with Ubuntu by default)/

---

