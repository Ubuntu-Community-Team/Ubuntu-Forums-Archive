---
title: "List of packages installed on top of base system"
date: 2006-09-24
forum: Desktop Environments
---

### Post by perrygeo on 2006-09-24
I've been happily using Dapper as my primary desktop OS at home on a pretty old machine and the time has come to upgrade hardware. I've installed hundreds of extra packages and I'm trying to find the easiest way to install all of them on my new machine.

So my plan is to get a list of all the packages I have installed on top of the base ubuntu packages. This way I can just do one big apt-get command and have my new system up and running with everything I need.

I've tried using 
```
dpkg --get-selections

``` 
which gives me a list of ALL my installed packages. This is a start but there are two problems:

- I have some packages that come straight from 3rd party debs that aren't in the repositories.
- The packages in the base system are also included.

Does anyone know of a good bash command to generate the list of ubuntu packages that have been installed *after* the base system??

---

### Post by Ramses de Norre on 2006-09-24
Just include them all? Aptitude wont make problems about it.

---

