---
title: "messed up installing java - jre; closed terminal"
date: 2009-02-24
forum: General Help
---

### Post by nikhil17 on 2009-02-24
Hi,

I was trying to install jave -jre (to use my school's web based vpn) and used instructions from [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-java-on-ubuntu-8.10-intrepid-ibex-688705/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-java-on-ubuntu-8.10-intrepid-ibex-688705/)).

The command I used was :
    sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

However, I accidently closed the terminal during the installation - I had a page that showed some stuff with an ok at the bottom when my terminal was closed(within the terminal only). 

Trying to re-run the same command gives me this message:
nikhil@nikhil-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Would really appreciate any help.
Thanks,
Nikhil

ps:  synoptic gives me the same message. More specifically:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Wayne_V on 2009-02-24
Did you try running 'dpkg --configure -a' ?   That should fix it.

If not, you could try:

apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts
apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by nikhil17 on 2009-02-24
Thanks for the reply. It is asking if I am root....how do I become root? use su instead of sudo?


> **Wayne_V said:**
> Did you try running 'dpkg --configure -a' ?   That should fix it.

If not, you could try:

apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts
apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by nikhil17 on 2009-02-24
Thanks for the reply. It asks me if I am root.....how do I become root?  use su instead of sudo?

---

### Post by todak on 2009-02-24
Type ***sudo**** dpkg --configure -a* in a terminal. Anything that asks if you are root means you forgot to prepend your command with **sudo**. ;)

---

### Post by nikhil17 on 2009-02-24
Sorry for multiple replies.  It asked for root privleges since I forgot to put sudo before the command. Thanks....now I will try installing jre again.

---

### Post by taurus on 2009-02-24
If you install it from a terminal, you need to accept the license before it will install.  So when you get to the license screen, press the Tab key to highlight the <OK> and Return to accept it.

---

