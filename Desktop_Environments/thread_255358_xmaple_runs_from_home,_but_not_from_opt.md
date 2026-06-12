---
title: "xmaple runs from /home, but not from /opt?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Joey French on 2006-09-11
Hi,
I have been trying to clean up my home folder by moving apps I have installed from tarballs, etc... into my /opt directory. I have had maple 9.5 installed for a long time now, in my home directory, and it runs well in classic, commandline, x, etc. However, I reinstalled the program to the /opt/maple9.5 directory using the howto on this forum's wiki, and for the life of me, I cannot get xmaple to run! "Classic" runs from this directory, as does "Commandline", but when I call xmaple using any method, it does nothing and returns me to the shell prompt. This is extremely frustrating, as I am certain that I have permissions set correctly, all files installed in the right places and so on.

Anyone have a clue why this would be?

Thanks,
Joey French

---

### Post by taurus on 2006-09-11
Maybe there is a link somewhere pointing to your home directory!!!  Did you put /opt/maple9.5/bin in your path?  Type this at the prompt and see what happen...

```

sudo find / -name xmaple -print

```

---

### Post by Joey French on 2006-09-13
It appears at some point I have symlinked the command /opt/maple9.5/bin/xmaple to /home/joey/maple9.5/bin/xmaple. I neeed to do a search and find how to remove a symlink. Thanks for the help.

Joey French

---

