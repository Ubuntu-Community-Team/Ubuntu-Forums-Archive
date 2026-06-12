---
title: "manpages don't work"
date: 2005-10-30
forum: Desktop Environments
---

### Post by mcpish on 2005-10-30
Hi, I seem to be having an issue with the manpages.  Everytime I use the "man" command to read the instructions for something I get:

man
bash: man: command not found

I checked in synaptec and I have the "manpages" package installed.  Is there something else I need to do?

---

### Post by aysiu on 2005-10-30
*man* needs a second part. For example, if you want to read the manpages for apt-get, you type ```
man apt-get
``` You can't just type ```
man
```

---

### Post by mcpish on 2005-10-30
no no I know that ;-) 
When I type man with "any" command i get the same message:

man apt-get
bash: man: command not found

---

### Post by aysiu on 2005-10-30
What happens when you type this in? ```
sudo apt-get install man-db
```

---

### Post by mcpish on 2005-10-31
> sudo apt-get install man-db
Password:
Reading package lists... Done
Building dependency tree... Done
man-db is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I know it's strange.  It seems like it's installed but the man pages just don't work for any command.

---

### Post by mcpish on 2005-10-31
okay I fixed the problem, thanks for putting me on the right track.  You were right it is the man-db program.  dpkg and synaptec says it was installed properly but just to give it a try.. I chose the "re-install" option in synaptec for the man-db package and that seemed to fix it.  There must have been some sort of missing file or misconfiguration.   Thanks =]

---

