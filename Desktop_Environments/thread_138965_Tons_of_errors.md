---
title: "Tons of errors"
date: 2006-03-02
forum: Desktop Environments
---

### Post by jnimble on 2006-03-02
I can't seem to get anything to work under Linux!

First I tried to get the cedega trial to work and heres what I got:

```
jnimble@ubuntu:~/Desktop$ sudo sh ./cedega_timedemo_installer
Verifying archive integrity... All good.
Uncompressing Cedega Time Demo....................................................................................................................................................................................................
/home/jnimble/.setup10086: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
So then i figured oh well let me try Wine. So I started following [this guide]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine"). Anyway, to make sure I had all the requirements I did this

```
jnimble@ubuntu:~$ sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```
and realized I needed to install msttcorefonts. So I tried to do that and that failed as well

```
jnimble@ubuntu:~$ sudo apt-get install msttcorefonts Reading package lists... Done Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```
I could really use some help here guys, thanks in advance!

---

### Post by Xian on 2006-03-02
Well, msttcorefonts is in the multiverse repo. 
Do you have that enabled??

[How-To Add Repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by jnimble on 2006-03-02
I just followed the guide exactly and it added 25-30 packages, but msttcorefonts was not one of them. Any other ideas?

I really appreciate the help btw :)

---

### Post by Xian on 2006-03-02
Download the [msttcorefonts](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_1.2ubuntu2_all.deb) package to your home directory and install with the dpkg command.

$ sudo dpkg -i msttcorefonts_1.2ubuntu2_all.deb

---

### Post by akiro.yamamoto on 2006-03-03
You can add the PLF repo as well. That has some of the resticted packages you may need.

---

### Post by Xian on 2006-03-03
Here is [INFO](http://wiki.ubuntu-fr.org/doc/plf) on the PLF repo.

---

### Post by jnimble on 2006-03-03
Wow, this is weird. The plf repository still didn't have the msttcorefonts package so I downloaded the .deb file and tried to run that but got a dependancy error because I didn't have cabextract. So then I did sudo apt-get install cabextract and it started installing the msttcorefonts with cabextract by itself. Is this normal functionality of apt?

---

### Post by Xian on 2006-03-03
[QUOTE=jnimble]Is this normal functionality of apt?[/QUOTE]

I'm still trying to figure out why it wasn't available when you added the multiverse repo. It either has to be a problem with your source list or the apt cache didn't update properly.

---

### Post by deathbyswiftwind on 2006-03-08
as far as cedega just " sudo apt-get install libgtk "

---

