---
title: "Can't install Compiz plugins from git? :("
date: 2010-11-07
forum: Desktop Environments
---

### Post by JaradT on 2010-11-07
I'm trying to install the freewins plugin for Compiz. Problem is, make won't let me.

```
jarad@JaradUbuntu:~$ mkdir compiz
jarad@JaradUbuntu:~$ cd ~/compiz
jarad@JaradUbuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/warlock/freewins
Initialized empty Git repository in /home/jarad/compiz/freewins/.git/
remote: Counting objects: 1208, done.
remote: Compressing objects: 100% (1204/1204), done.
remote: Total 1208 (delta 831), reused 0 (delta 0)
Receiving objects: 100% (1208/1208), 305.04 KiB | 56 KiB/s, done.
Resolving deltas: 100% (831/831), done.
jarad@JaradUbuntu:~/compiz$ cd freewins
jarad@JaradUbuntu:~/compiz/freewins$ make
make: *** No targets specified and no makefile found. Stop.
later on--
jarad@JaradUbuntu:~/compiz/freewins$ make CMakeLists.txt
make: Nothing to be done for `CMakeLists.txt'.
jarad@JaradUbuntu:~/compiz/freewins$ make freewins.xml.in
make: Nothing to be done for `freewins.xml.in'.

```anything i'm doing wrong?

---

### Post by JaradT on 2010-11-07
Can someone help?

---

### Post by JaradT on 2010-11-07
Is there anything I'm doing wrong? Please, PLEASEEE help me :(

---

### Post by JaradT on 2010-11-07
Help me! I tried the tutorials and everything!

---

### Post by Banned. on 2010-11-07
Hello,

CMakeLists.txt cannot be used by make.

```
sudo apt-get install cmake
mkdir build
cd build
cmake ..
make
sudo make install
```

If you are compiling compiz then after this
```
sudo make findcompiz_install
```

If you are compiling compizconfig
```
sudo make findcompizconfig_install
```

---

### Post by JaradT on 2010-11-08
> **Banned. said:**
> Hello,

CMakeLists.txt cannot be used by make.

```
sudo apt-get install cmake
mkdir build
cd build
cmake ..
make
sudo make install
```If you are compiling compiz then after this
```
sudo make findcompiz_install
```If you are compiling compizconfig
```
sudo make findcompizconfig_install
```

I have compiz and compizconfig, I need to install some plugins installed with git.

---

### Post by Decatf on 2010-11-08
For one thing that plugin is for Compiz 0.9.x which is now completely incompatible with previous versions. Maverick is using Compiz 0.8.x. You'll want to get the 0.8 version but doing **git checkout compiz-0.8** and doing the git clone.

Also bumping your thread like a madman is usually detrimental to your cause.

---

### Post by Banned. on 2010-11-08
You can do the same with plugins, too!

---

### Post by JustinR on 2010-11-08
I ran into this same problem yesterday!

Here is a script that has all of the experimental plugins, including 'freewins'. Freewins doesnt do much though - you can't interact with a window after you have moved it. And it freezes compiz often.

[http://forum.compiz.org/viewtopic.php?f=114&t=12012](http://forum.compiz.org/viewtopic.php?f=114&t=12012)

---

### Post by JOHNNYG713 on 2010-11-09
Try this ! [http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32+%26+64+Bit?content=118511](http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32+%26+64+Bit?content=118511)

---

