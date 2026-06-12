---
title: "HP Officejet 7210 Scanner"
date: 2007-08-05
forum: Desktop Environments
---

### Post by Magiczero on 2007-08-05
Hi

I've got a networked HP Officejet 7210 and I've got it printing in color but, I can't get the scanner to work in ubuntu it works in XP on other systems.  How do I get it to work in ubuntu?  Is there a program i need to install?

---

### Post by pbcartwright on 2007-08-06
HP Printers / Scanners are normally no problem - best is you check [http://www.linuxprinting.org/](http://www.linuxprinting.org/) - there you get a lot of information and hints. 
and checkout the sourceforge HP printing project and look into :
sane/xsane hplijs hplip the HP linux printer drivers

---

### Post by joeythedog on 2007-10-08
okay well that stuff is somewhat  helpful, but not until i read like 50 pages
of various crap from the links above... try 
$ hp-setup

to save some unnecessary reading

ps. those responses i've seen in other threads of "try google" are not only not helpfull, but they aren't funny either... obviously i've tried google... thats how i found this damn page...
thanks

---

### Post by yclian on 2007-11-02
Hi guys,

I managed to get my Office Jet 7200 to do scanning after reading this thread, basically what I did was:

1. apt-get install python-qt3 (required for the GUI of hp-setup)
2. Run hp-setup (hp-setup is the HP Linux Imaging and Printing System)
3. Run xsane

:-)

yc

---

