---
title: "Make hates me."
date: 2009-03-29
forum: General Help
---

### Post by moosehadley on 2009-03-29
Ok, well, trying to create a cluster with a program called Kerrighed.
It had me make a patched kernel, and all that went fine.
And then, I tried to make the actual program, I keep getting this:

```
{user}@{user}-desktop ~/Desktop/kerrighed-2.3.0 $ make 
Making all in modules
make[1]: Entering directory `/home/{user}/Desktop/kerrighed-2.3.0/modules'
rm -f "/home/{user}/Desktop/kerrighed-2.3.0/modules/asm"
[ "/home/{user}/Desktop/kerrighed-2.3.0" == "/home/{user}/Desktop/kerrighed-2.3.0" ] || lndir -silent "/home/{user}/Desktop/kerrighed-2.3.0/modules"
[: 1: ==: unexpected operator
/home/{user}/Desktop/kerrighed-2.3.0/modules: From and to directories are identical!
make[1]: *** [all-y] Error 1
make[1]: Leaving directory `/home/{user}/Desktop/kerrighed-2.3.0/modules'
make: *** [all-recursive] Error 1

```

---

### Post by mhgsys on 2009-03-29
have you tried sudo make?

---

### Post by moosehadley on 2009-03-29
Yes, I have, exact same error

---

### Post by mhgsys on 2009-03-29
Well, Sorry to say:
I can't help you out very much since I don't use make very often, 

However the error :From and to directories are identical!

Seems pretty clear to me, if I understand correctly.
  
My thought is that you should change the "to directory",but since I don't use make often I don't know the commando to do that.

I suggest you read 
```

man make

```

or maybe someone else can help you further, 

good luck anyway.

---

### Post by hyper_ch on 2009-03-29
don't make it in the same dir... make a build dir and then run configure, make and make isntall from there... or is ith cmake isntead of configure?

---

### Post by Rallg on 2009-03-29
Look in the package of source code. Usually, there are text files that explain any tricks that must be used during compilation. The files might be "INSTALL" or some other obvious name. It may be that you need to pass a parameter (or set an environment) into the make process.

---

### Post by r.stiltskin on 2009-03-29
It seems that you may need to use gcc-3.3 to build kerrighed.

There's some discussion of that error here:
[http://ubuntuforums.org/showthread.php?t=1030849&page=11](http://ubuntuforums.org/showthread.php?t=1030849&page=11)

---

### Post by hyper_ch on 2009-03-29
if I may point out:

> 
/home/{user}/Desktop/kerrighed-2.3.0/modules: From and to directories are identical!


---

### Post by r.stiltskin on 2009-03-29
> **hyper_ch said:**
> if I may point out:Quote:
/home/{user}/Desktop/kerrighed-2.3.0/modules: From and to directories are identical! 

Yes, that is precisely the error that other people experienced and the cause apparently was that they were using gcc-4.2.x while the build required 3.3

---

### Post by moosehadley on 2009-03-29
Ok, cool, so I got gcc-3.3 from apt.
How do I make 'make' use it?

---

### Post by r.stiltskin on 2009-03-29
This will change your default gcc version to 3.3:
```

sudo ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc
sudo ln -sf /usr/bin/g++-3.3 /usr/bin/g++
```

When you're finished using 3.3 & want to switch back to 4.3:
```

sudo ln -sf /usr/bin/gcc-4.3 /usr/bin/gcc
sudo ln -sf /usr/bin/g++-4.3 /usr/bin/g++
```
(or 4.2 -- whichever version you have installed.)

Then you should probably cd back into your ~/Desktop/kerrighed-2.3.0 directory & run "make uninstall" and "make clean" to get rid of any components that were compiled earlier, and then start the build process again beginning with ./configure ...

PS: look at this guide for installing kerrighed in ubuntu 8.04:
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

---

### Post by moosehadley on 2009-03-29
I'm just getting the exact same error

---

### Post by hyper_ch on 2009-03-29
well, IMHO the error message is clear... but nobody wants to listen...

---

### Post by r.stiltskin on 2009-03-29
Did you follow this instruction (from the link that I posted in #7)?  In particular, note the "-i" option in
make -i
and
make install -i

> I followed the same procedure as the guide on Easy Ubuntu Clustering, but the following was different in the kerrighed install:

```


sudo apt-get install subversion
svn checkout svn://scm.gforge.inria.fr/svn/kerrighed/trunk /nfsroot/kerrighed/usr/src/trunk -r 4762
sudo chroot /nfsroot/kerrighed
apt-get install automake autoconf libtool pkg-config gawk rsync bzip2 gcc-3.3 ncurses-dev wget lsb-release xmlto patchutils xutils-dev build-essential grub g++-3.3
cd /usr/src/trunk
./autogen.sh
./configure CC=gcc-3.3 CXX=g++-3.3
make defconfig
cd kernel
make menuconfig
cd ..
make kernel
make -i
make kernel-install
make install -i
```

I'll update the wiki soon so that it details how to install the SVN version too. In later revisions from the svn, you can drop the -i flag, as they seem to have corrected the src folder == dest folder issue.

---

### Post by r.stiltskin on 2009-03-29
> **hyper_ch said:**
> well, IMHO the error message is clear... but nobody wants to listen...

Nobody's ignoring you.  The error is clear; the problem is how to fix it.

---

### Post by heindsight on 2009-03-29
I suspect your problem is here:
> **moosehadley said:**
> 
```

[ "/home/{user}/Desktop/kerrighed-2.3.0" **==** "/home/{user}/Desktop/kerrighed-2.3.0" ] || lndir -silent "/home/{user}/Desktop/kerrighed-2.3.0/modules"
**[: 1: ==: unexpected operator**

```

```
[ "/home/{user}/Desktop/kerrighed-2.3.0" == "/home/{user}/Desktop/kerrighed-2.3.0" ] || lndir -silent "/home/{user}/Desktop/kerrighed-2.3.0/modules"
```
Is supposed to only run lndir if two directories (I'm guessing the source and build directories) are not the same. Since, in your case the directories are the same, lndir shouldn't run. However, the test to check whether the directories are the same is failing and so lndir is running when it shouldn't (causing an error, which stops make).

I suspect the problem is that the Makefile assumes that /bin/sh is bash (== is a bashism). To fix the problem, you'll have to edit the Makefile to have it explicitly use /bin/bash rather than /bin/sh. You can do this by editing the Makefile and adding a line like:
```
SHELL=/bin/bash
```
near the top of the Makefile.

---

### Post by robasc on 2009-04-13
Hello heindsight, I am having the same problem with the identical error deal. Could you tell me how to get to the make file?

---

### Post by heindsight on 2009-04-19
> **robasc said:**
> Hello heindsight, I am having the same problem with the identical error deal. Could you tell me how to get to the make file?
In the directory where you're running make, there should be a file called Makefile.

---

