---
title: "Compiler on Ubuntu 6.06"
date: 2006-06-15
forum: Desktop Environments
---

### Post by woodland on 2006-06-15
It seems that there is no C compiler in my installation.  I did a search
for "C compiler", but the search didn't work since it won't accept one
character search terms.

How do I install a C compiler?  Why on earth isn't it included by default?

---

### Post by bruce89 on 2006-06-15
```
sudo apt-get install build-essential
```
[QUOTE=woodland]Why on earth isn't it included by default?[/QUOTE]
Ubuntu is only 1 CD, it would waste space, there is debate on this though - [http://www.ubuntuforums.org/showthread.php?t=192840](http://www.ubuntuforums.org/showthread.php?t=192840)

---

### Post by Sutekh on 2006-06-15
Actually it is included by default, build-essential (and the packages it installs)  *is* on the CD.  However it is not installed by default.

Depending on your intentions you may only need the GNU C compiler itself, rather thn the build tools in build-essential
```
sudo apt-get install gcc
```

---

### Post by damiendusha on 2006-06-15
Hello,

I have tried this, but I have a small problem:

damien@BEE-00002630:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc

damien@BEE-00002630:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential

Which is funny because the synaptic packet manager says it's installed.

So I don't know that I am doing wrong.

I thought I did a full install of ubuntu....???

---

### Post by Sutekh on 2006-06-15
What are your repository sources?
```
cat /etc/apt/sources.list
```

---

