---
title: "vmware-install.pl"
date: 2005-11-26
forum: Desktop Environments
---

### Post by tellnes on 2005-11-26
Hey,
probably a stupid question, anyway..

I wanna run vmware un my ubuntu box, i have read alot about it and how to install it, i have downloaded kernel header files, and should be ready to go..
But when i try to ./vmware-install.pl nothing happens, doesent run the script.
Do i have to install some additional pearl packages? I have the basic, default perl  packages, what do i needto get the script to lauch.
Doing it as root btw..

txh

-t-

---

### Post by ShakingSpirit on 2005-11-26
What do you mean by 'doesn't run'? Is there an error? Does running 'perl vmware-install.pl' work?

---

### Post by msr7x57 on 2005-11-26
Is ./vmware-install.pl executable?

If it isn't try "sh ./vmware-install.pl".

If that doesn't help, you're going to have to give us a few clues, like what the messages are, f'rinstance.

HTH

---

### Post by plb on 2005-11-26
sudo ./vmware-install.pl

?

---

### Post by MartinG on 2005-11-26
What error messages are you getting? Try this thread -- this covers the usual problems (in particular, the matter of which compiler you're using):

[http://www.ubuntuforums.org/showthread.php?t=77040](http://www.ubuntuforums.org/showthread.php?t=77040)

---

