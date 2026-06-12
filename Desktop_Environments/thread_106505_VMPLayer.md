---
title: "VMPLayer"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Taranis on 2005-12-20
I'm attempting to install VMplayer from VMware on 5.10 and getting the following...

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes] 
__________________________________________

Any thoghts?
TIA

---

### Post by zoiks on 2005-12-21
I think you should start with a

```
sudo apt-get install build-essential
```

at a command prompt.  I believe that installs the compilers you need, though it's possible you might have to apt-get install other things.

---

### Post by mrgraz on 2006-05-28
[QUOTE=zoiks]I think you should start with a

```
sudo apt-get install build-essential
```

at a command prompt.  I believe that installs the compilers you need, though it's possible you might have to apt-get install other things.[/QUOTE]


[COLOR="Blue"]I was having the same problem and I opened up a new terminal and ran "sudo apt-get install build-essential"  and after everthing got done intstalling from that command the VMWare tools installed with out a problem.  

Thanks for the information[/COLOR] =D>

---

