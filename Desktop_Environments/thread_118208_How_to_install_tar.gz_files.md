---
title: "How to install tar.gz files ?"
date: 2006-01-16
forum: Desktop Environments
---

### Post by pfabrikant on 2006-01-16
Hey,
I downloaded the amule version for linux. What is the command line to  install the tar.gz files ?
Thanks

---

### Post by enetic on 2006-01-16
"tar zxvf /path/to/file.tar.gz" Example:
tar zxvf /home/yoyo/file.tar.gz

correct me if im wrong. im a noob, but try that.

---

### Post by greenpenguin on 2006-01-16
.tar.gz files are source archives, which are a pain to install.  I would advise installing amule from the repositories - you'll have to enable the universe repos (guides out there somewhere :D).  You can install the .tar.gz packages:
[LIST=1]
[*]Extract the file somewhere
[*]Read the README and INSTALL files
[*]Install any packages you're missing through synaptic
[*]do what the INSTALL file says - probably this:[/LIST]```
./configure
make
sudo make install
```

Not worth the effort usually :P.

---

### Post by pfabrikant on 2006-01-16
hey, how do I enable the universal repositories ?

---

### Post by lnxpwr on 2006-01-16
uncomment the lines for "universe" in the /etc/apt/sources.list file with your prefered editor (e.g  sudo vi /etc/apt/sources.list)

---

### Post by PuNGS on 2006-01-16
And with extra repositories you can install it from synaptic.

---

### Post by pfabrikant on 2006-01-16
I'm really new with linux so I didn't undestand anything in the two last replies..
How do I add repositories in the sinaptic ?
How do I uncomment the  sources.list, and what is my favourite editor ?
I'm lost

---

### Post by Gandalf on 2006-01-16
[QUOTE=greenpenguin].tar.gz files are source archives, which are a pain to install.  I would advise installing amule from the repositories - you'll have to enable the universe repos (guides out there somewhere :D).  You can install the .tar.gz packages:
[LIST=1]
[*]Extract the file somewhere
[*]Read the README and INSTALL files
[*]Install any packages you're missing through synaptic
[*]do what the INSTALL file says - probably this:[/LIST]```
./configure
make
sudo make install
```

Not worth the effort usually :P.[/QUOTE]
Just for info
Instead of using make install, please use checkinstall this will create a deb package that can be installed by dpkg..
```

sudo apt-get install checkinstall

```

```

sudo checkinstall -D

```
answer the questions asked, a deb file will be created 
```

sudo dpkg -i file_name.deb

```

---

### Post by aysiu on 2006-01-16
[QUOTE=pfabrikant]
How do I add repositories in the sinaptic ?
How do I uncomment the  sources.list, and what is my favourite editor ?
I'm lost[/QUOTE] The first link of my signature has step-by-step instructions.

---

