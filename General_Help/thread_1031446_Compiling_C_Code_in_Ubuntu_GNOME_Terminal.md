---
title: "Compiling C Code in Ubuntu GNOME Terminal"
date: 2009-01-05
forum: General Help
---

### Post by throlkena on 2009-01-05
Hi, I am new to using the C Compiler in linux.

Now, this is my problem really:

//i am trying to compile this:  a.c

#include <stdio.h>
#include <sys/types.h>

int main()
{
     fork();
     print("Hello Fork!\n");
}



//then i compile and link using : gcc -o proc1 a.c
//then run as ./proc1


//the errors:

/*
a.c:1:20: error: stdio.h: No such file or directory
a.c:2:22: error: sys/types.h: No such file or directory
a.c: In function ‘main’:
a.c:7: warning: incompatible implicit declaration of built-in function ‘printf’
*/


If anyone knows how to workaround this, or if there's anyother way to do this, please do let me know,

This worked in a terminal i used at university, but it doesn't work in the emulator on my laptop.

---

### Post by kanikilu on 2009-01-05
Do you have the build-essential package installed?

```
sudo apt-get install build-essential
```

---

### Post by throlkena on 2009-01-05
i get this error trying to install:

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
 Depends: dpkg-dev but it is not going to be installed

---

### Post by kanikilu on 2009-01-05
According [to this thread]("http://ubuntuforums.org/showthread.php?t=308691"), try using aptitude instead of apt-get:

```
sudo aptitude install build-essential
```

---

### Post by throlkena on 2009-01-05
> **kanikilu said:**
> According [to this thread]("http://ubuntuforums.org/showthread.php?t=308691"), try using aptitude instead of apt-get:

```
sudo aptitude install build-essential
```



that made some progress, but now it's asking for the gutsy cd, which unfortunately i do not have. is there anyway i can download the package from the internet?


--
this: :(

Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libc6-i686
ubuntu-minimal

Install the following packages:
dpkg-dev [1.14.5ubuntu16 (gutsy, gutsy)]
g++ [4:4.1.2-9ubuntu2 (gutsy, gutsy)]
g++-4.1 [4.1.2-16ubuntu2 (gutsy, gutsy)]
libc6-dev [2.6.1-1ubuntu9 (gutsy, gutsy)]
libstdc++6-4.1-dev [4.1.2-16ubuntu2 (gutsy, gutsy)]

Keep the following packages at their current version:
g++-4.2 [Not Installed]
libstdc++6-4.2-dev [Not Installed]

Downgrade the following packages:
libc6 [2.6.1-1ubuntu10 (now) -> 2.6.1-1ubuntu9 (gutsy)]

Score is -294

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  ant ant-optional eclipse-rcp libarkrpg0c2a libbcel-java libbcprov-java 
  libcairo-java libcairo-jni libcommons-beanutils-java libcommons-cli-java 
  libcommons-collections-java libcommons-collections3-java 
  libcommons-dbcp-java libcommons-digester-java libcommons-el-java 
  libcommons-launcher-java libcommons-logging-java libcommons-modeler-java 
  libcommons-pool-java libcurl3 libglib-java libglib-jni libgnucrypto-java 
  libgtk-java libgtk-jni libjsch-java liblog4j1.2-java liblua40 liblualib40 
  liblucene-java liblucene-java-doc libmx4j-java libregexp-java 
  libsdl-console libsdl-gfx1.2-4 libseda-java libsmpeg0 libswt3.2-gtk-java 
  libswt3.2-gtk-jni libxml++2.6c2a 
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following packages will be automatically REMOVED:
  libc6-i686 ubuntu-minimal 
The following packages will be DOWNGRADED:
  libc6 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following packages will be REMOVED:
  libc6-i686 ubuntu-minimal 
0 packages upgraded, 6 newly installed, 1 downgraded, 42 to remove and 0 not upgraded.
Need to get 0B/11.4MB of archives. After unpacking 7057kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press [Enter].

---

### Post by donkyhotay on 2009-01-05
Looks like your sources are pointing towards the CD when it should be pointing to the internet can you post your /etc/apt/sources.list file?

---

### Post by throlkena on 2009-01-05
> **donkyhotay said:**
> Looks like your sources are pointing towards the CD when it should be pointing to the internet can you post your /etc/apt/sources.list file?

Okay. Taking your hint, i removed the CDs from the software sources. And then it worked! thanks.

and i thank you kanikilu as well!

:D


EDIT: can't believe i just downgraded my OS! :P

---

