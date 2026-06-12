---
title: "Broken package manager---update output"
date: 2013-01-10
forum: Desktop Environments
---

### Post by psyllex on 2013-01-10
My package manager is straight busted!  It says:


```
The following packages have unmet dependencies:
 bandwidthd:i386 : Depends: ucf:i386 but it is not installable
 libpcap-dev : Depends: libpcap0.8-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

But it's not specific to the libpcap0.8-dev package...it says that for everything in some form or another.  Here is the output for ```
sudo apt-get upgrade
```:


```
psyllex@psyllex-pc:~/downloads/bandwidthd-2.0.1$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```


I read through some other posts on this but haven't found anything that has fixed the problem?  Much appreciated.

---

### Post by ibjsb4 on 2013-01-11
What about  apt-get -f install?

---

