---
title: "PHP Apache Mysql installed or not, and where"
date: 2009-04-19
forum: General Help
---

### Post by runnner on 2009-04-19
How do I know if PHP Apache Mysql installed or not, if they are installed already, how can I find where they are installed? How can I do these in a terminal window? Thanks for help!

---

### Post by Tim Sharitt on 2009-04-19
If you have installed them from the repos (or a .deb file), you can see where all the files are installed to with dpkg -L [package-name]

For a complete listing of the apache2.2-common package
```
dpkg -L apache2.2-common
```

or to just see if it is installed
```
dpkg -l apache2.2-common
```

Alternately, which may work for a quick check

```
which apache2
```

---

### Post by runnner on 2009-04-19
This is what I got. I don't know what the results mean.


root@ubuntu:~# dpkg -l apache2.2-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  apache2.2-comm 2.2.8-1        Next generation, scalable, extendable web se

---

### Post by Tim Sharitt on 2009-04-19
apache2 is installed. If a package is not installed, you should get some thing like

```
No packages found matching [package-name]
```

---

