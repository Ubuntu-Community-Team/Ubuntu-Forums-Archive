---
title: "is it just me?"
date: 2008-12-19
forum: General Help
---

### Post by luposolo on 2008-12-19
is it just me or does ubuntu 8.10 use alot of cpu usage when running only few applications

---

### Post by mssever on 2008-12-19
> **luposolo said:**
> is it just me or does ubuntu 8.10 use alot of cpu usage when running only few applications
"Ubuntu" doesn't use any CPU. The programs installed do. If you look in System Monitor, you can see what's really happening. Note, however, that System Monitor itself uses a fair amount of CPU.

---

### Post by donkyhotay on 2008-12-19
System monitor is ok for determing if there is a problem but because it's relatively resource intensive for a monitor it usually isn't the best option for finding troublesome programs. I would recommend top in a terminal as you use your computer and keep an eye on whats going on that way. Top is pretty easy to run just go 
```
top
```
in the terminal and it will show the top ten processes along with the CPU and RAM percentage.

---

### Post by mssever on 2008-12-19
> **donkyhotay said:**
> Top is pretty easy to run just go 
```
top
```in the terminal and it will show the top ten processes along with the CPU and RAM percentage.
For that matter, htop is far better than top. I always use htop for this kind of troubleshooting.

```
sudo aptitude install htop
```Like top, htop has to run inside a terminal, although it does provide an icon in your menus so you don't have to mess with a terminal if you don't want to.

---

