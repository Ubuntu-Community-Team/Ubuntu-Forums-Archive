---
title: "ADDED WRONG LINK TO SOURCE. CAN'T EDIT NOW. HELP n00b in trouble."
date: 2006-08-24
forum: Desktop Environments
---

### Post by Samo_Filling on 2006-08-24
E: Type 'http://packages.freecontrib.org/ubuntu/plf/' is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


This is error message that pops up when i load Synaptic.


**also, with VMware, could i install windows 98se? emulating that with ubuntu as the main?**

---

### Post by gatiba on 2006-08-24
Simply open a shell and type:

```
sudo gedit /etc/apt/sources.list
```

and manually remove line 52.

---

### Post by Jucato on 2006-08-24
I would like to correct that with

```
gksudo gedit /etc/apt/sources.list
```

as for the VMWare questions, yes it's possible, as far as I know.

Next time, please try not to shout (all CAPS) or double post. :D

---

### Post by master_b on 2006-08-24
Open /etc/apt/sources.lst in a text editor ( I usually use kate) as root -sudo kate -

your required entry should be:-

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

notice the deb in front and the (space)dapper free non-free

just cut and paste to correct your list. Don't forget to hit return after entering the line

Bill

---

