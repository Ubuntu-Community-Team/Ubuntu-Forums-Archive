---
title: "Can't ./configure"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Kensi on 2005-10-27
I want to compile something from source, but 

./configure

gives

bash: ./configure: No such file or directory

what pakage do I need to install to be able to use configure? On past systems I used it was present.

---

### Post by 23meg on 2005-10-27
make sure you have build-essential installed. some software may not require ./configure before compilation; always take a look at the readme file that comes in the tarball before compiling

---

### Post by aysiu on 2005-10-28
First of all, make absolutely sure you can't just install the package through Synaptic (see the second link in my sig). If you must install from source, make sure you have *build-essential*: Just type this in a terminal ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by cwaldbieser on 2005-10-28
[QUOTE=Kensi]I want to compile something from source, but 

./configure

gives

bash: ./configure: No such file or directory

what pakage do I need to install to be able to use configure? On past systems I used it was present.[/QUOTE]
It actually sounds like there is no "configure" script in your current directory when you try to run it.

---

