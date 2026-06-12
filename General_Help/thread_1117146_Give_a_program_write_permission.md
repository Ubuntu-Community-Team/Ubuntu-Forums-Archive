---
title: "Give a program write permission"
date: 2009-04-05
forum: General Help
---

### Post by pmuller on 2009-04-05
Hello,

I'm fairly new to ubuntu linux. I'm using a program called Mesquite (phylogenetics program) and it wants to keep a log in /home/muller which is necessary for propper function. I've given this folder write permissions (chmod 777) but Mesquite still can't make a log. How can I go about giving this program the write permissions it needs?

Thank you very much,
Paul

---

### Post by pastalavista on 2009-04-05
your home folder should have had write permissions from the start. I think maybe you need to change the owner of Mesquite to muller

---

### Post by |Porsche on 2009-04-05
ARe you sure Mesquite is attempting to write the log file to your home folder?

---

### Post by pmuller on 2009-04-05
I made the owner of Mesquite muller:muller (recursively) and I'm still having the problem. I've posted the warning message below. Thanks.

"Mesquite does not have permission to write its log file.  This may indicate issues with your system configuration that will prevent Mesquite from functioning properly.  Please check that your system permits Mesquite to write to /home/muller"

---

### Post by pastalavista on 2009-04-05
run ```
gksu nautilus
``` you are now in super-user mode so be careful. right-click the files and folders you are using, select 'properties' and set the permissions with the GUI. Then log out and log back in.

I'm a relative novice... that's all I got... it has worked for me before in permissions problems

---

