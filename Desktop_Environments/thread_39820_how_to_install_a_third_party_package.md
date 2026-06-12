---
title: "how to install a third party package?"
date: 2005-06-06
forum: Desktop Environments
---

### Post by xo310 on 2005-06-06
I downloaded xchm package (for ubuntu) to my desktop. I know that command # dpkg -i [package].. But this will tell me no such file or di&#287;rectory. 
Where should I put packages I download to access for installation.

It is really frustrating to know that installation is not yet automatic like in win

---

### Post by tyze on 2005-06-06
Try this...

Go into a console (terminal)..
and type:

- su
- *enter password*
- cd "dir" <-- directory containing the package
- chmod +x "Packagename"
- dpkg -i "Packagename"

---

### Post by xo310 on 2005-06-06
5 lines to install this package?
thank you

---

### Post by SGC on 2005-06-06
[QUOTE=xo310]5 lines to install this package?
thank you[/QUOTE]
 You can right click to install any packge:
**Ubuntu:** [http://ubuntuforums.org/showthread.php?t=33584](http://ubuntuforums.org/showthread.php?t=33584)
**Kubuntu:** [http://ubuntuforums.org/showthread.php?t=33440](http://ubuntuforums.org/showthread.php?t=33440)

---

### Post by tyze on 2005-06-07
1 line to become superuser, 1 line to go into the right direcotry, 1 line to set the right userrights on the package and 1 line to install it!

You can also do it in one line ;)

Start the Root-Terminal

and enter the following:

chmod +x /dir/packagename; dpkg -i /dir/packagename

just if you don't like to type it in 5 lines ;)

---

