---
title: "location for packages"
date: 2009-05-12
forum: General Help
---

### Post by jitsonfire on 2009-05-12
I am new to ubuntu. I would like to know where are the packages
downloaded when we use sudo apt-get cmd.
I have noticed for any program many packages are downloaded.
How do I know which order should I install them
Using the terminal.
thks for your help in advance.

---

### Post by plucky on 2009-05-12
> I would like to know where are the packages downloaded when we use sudo apt-get cmd.

From a terminal
```
ls /var/cache/apt/archives
```


> I have noticed for any program many packages are downloaded.
How do I know which order should I install them
Using the terminal.

The package manager will tell you when it needs a dependency installed,but I would recommend you use the Synaptic Package manager system or Add/Remove to install any further software, until you get more familiar with the linux software installation procedures.

Good Luck

---

### Post by Kevbert on 2009-05-12
If you use
```
sudo apt-get install *package*
```
or Synaptic Package Manager you should not need to worry about dependencies as these should be automatically looked after for you by these methods. In both cases the installer will tell you what additional packages will be installed.

---

