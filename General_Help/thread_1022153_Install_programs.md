---
title: "Install programs??"
date: 2008-12-26
forum: General Help
---

### Post by ibootindos on 2008-12-26
So I know how to untar a file, I know how to run an executable file, with permissions and stuff.. but I still can't get programs to work...? Like I'll untar it, run the config, and then what? If somebody could walk me through a step by step what if for untar'ing and installing and accessing a program, I'd be delighted :)

---

### Post by neu2buntu on 2008-12-26
there  should be 2 files README and INSTALL in the program folder these should help you. mostly the command after compiling is make and sudo make install after configuring

---

### Post by bodhi.zazen on 2008-12-26
Is there some reason you are installing from source ?

The Ubuntu repositories are quite large. See 

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by ibootindos on 2008-12-26
> **bodhi.zazen said:**
> Is there some reason you are installing from source ?

The Ubuntu repositories are quite large. See 

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Yes, I'm in iraq right now, I don't have internet hooked up to my laptop, the internet I'm using is at an internet cafe. But I have a lot of tar.gz programs on a DVD I have that I want to try and install from source.

---

### Post by bodhi.zazen on 2008-12-26
> **ibootindos said:**
> Yes, I'm in iraq right now, I don't have internet hooked up to my laptop, the internet I'm using is at an internet cafe. But I have a lot of tar.gz programs on a DVD I have that I want to try and install from source.

When you install from source you first need to install build-essential.

You then need to install all the dependencies, and often the development or so called "-dev" packages.

You then extract the archive and read the README

Most often

./configure --prefix=/usr/local
make
sudo make install

---

### Post by albinootje on 2008-12-26
> **ibootindos said:**
> Yes, I'm in iraq right now, I don't have internet hooked up to my laptop, the internet I'm using is at an internet cafe. But I have a lot of tar.gz programs on a DVD I have that I want to try and install from source.

If you didn't install the meta-package "build-essential" in Ubuntu already then you won't have much chance to compile and install anything at all.
And for some programs you might also need packages like flex, bison, automake, patch, and e.g. libgtk2.0-dev depending on what the source package needs.

It could be more interesting to burn a cdrom or DVD with Ubuntu packages with this software from the Internet cafe :
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

