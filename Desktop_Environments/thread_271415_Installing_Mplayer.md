---
title: "Installing Mplayer"
date: 2006-10-04
forum: Desktop Environments
---

### Post by AT-AT on 2006-10-04
I've got a problem. I dont like totem because it doesnt play many popular formats as far as I can tell, and I tried to install Mplayer. Well I went to the [site]("http://http://www.mplayerhq.hu/design7/dload.html") and the only package that looks like it would work with Ubuntu is the source itself. Which is just grate since Im new and have no clue as to how to install without one of those nifty installer programs. The 'readme' is a travesty as it doesnt actually tell you how to install it in terms somebody like me can understand. So I ask you, the Ubuntu community, if you guide me step by step about how to install Mplayer. Thanks in advance.

---

### Post by Anonii on 2006-10-04
1) [http://ubuntuforums.org/showthread.php?t=187709&highlight=compiling+mplayer](http://ubuntuforums.org/showthread.php?t=187709&highlight=compiling+mplayer)
2) ?????
3) PROFIT!!!

---

### Post by AT-AT on 2006-10-04
I always forget something. I meant to add that the computer I have ubuntu on isnt (and due to circumstances, cant be) connected to the net, so out goes what I've heard is the easiest way to install stuff on Ubuntu. Also (and I havent looked for it yet) apparently I dont have subversion because the terminal says the svn command is invalid.

---

### Post by Old Pink on 2006-10-04
Download from: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
Get it on the no-internet computer.
```

tar xzf <filename.tar.gz>
cd <created directory>
./configure
make
sudo make install

```

---

### Post by AT-AT on 2006-10-05
Okay so I entered these commands```
tar xzf <filename.tar.gz>
cd <created directory>
./configure
```
and the terminal told me "*** Please downgrade/upgrade C compiler to version gcc-2.95.x or gcc-3.x! ***". So I went and and I downloaded the files for gcc-3.4.6. I followed the instructions on that site and entered these commands
```
mkdir objdir
cd objdir
srcdir/configure
```
and the terminal told me "*** The command 'cc -o conftest -g conftest.c' failed. *** You must set the environment variable CC to a working compiler.". So what is an enviroment variable, and how do I set the CC enviroment variable to a working compiler?

---

