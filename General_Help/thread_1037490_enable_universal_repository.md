---
title: "enable universal repository"
date: 2009-01-11
forum: General Help
---

### Post by newbux on 2009-01-11
hello i am working on a tutorial and one of the things that your supposed to do is enable the universal repository and then run a command in the terminal and install some things. i dont know exactly what they want me to do when they say enable the repository can someone explain in detail what they mean thanks

---

### Post by taurus on 2009-01-11
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

That's where you enable universe, multiverse, and third party repos.

Otherwise, you can edit /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
```
and remove the # sign in front of all the lines that start with **deb** or **deb-src**.

---

### Post by newbux on 2009-01-11
thanks for the help

---

