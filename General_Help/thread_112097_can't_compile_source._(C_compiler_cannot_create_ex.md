---
title: "can't compile source. (C compiler cannot create executables)"
date: 2006-01-03
forum: General Help
---

### Post by JacksonL on 2006-01-03
Hey everyone. :) 

I'm trying to install wine. I entered the repository entry found on the wine site, but for some reason it has unresolved dependency problems (it won't download wine itself, only the graphical frontends and libs), so I decided to try compiling the source. I downloaded the source and followed the instructions, installing gcc, make, and bison. But whenever I try to compile I get the following error:
[SIZE="1"]```

jackson@jackson:~/Desktop/wine-0.9.4$ ./tools/wineinstall
WINE Installer v0.75

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

```[/SIZE]
I'm kind of a linux (and computers in general) noob altogether, so please don't say anything too complicated :D . I'm using the athlon 64 version of ubuntu 5.10. I get the same message when performing the operation as root.

---

### Post by GeneralZod on 2006-01-03
Try

```

sudo apt-get install build-essential

```

---

### Post by JacksonL on 2006-01-03
thank you very much for the help, but it still gives me the same error message :( . the package you recommended was installed correctly (supposedly. here's what it said:)
[SIZE="1"]```

jackson@jackson:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-4.0 libstdc++6-4.0-dev
Suggested packages:
  gcc-4.0-doc libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4077kB of archives.
After unpacking 15.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package libstdc++6-4.0-dev.
(Reading database ... 65431 files and directories currently installed.)
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.1-3_amd64.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_amd64.deb) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...

```[/SIZE]
again (just for clarity) it still displays the same error message that I mentioned in my first post when I do what I did in my first post.

---

### Post by JacksonL on 2006-01-03
I've also now tried installing the RPMs for glibc-devel 2.3.6_i386 and glibc-devel 2.3.6_x86_64. they didn't help anything.

---

### Post by RAOF on 2006-01-04
It looks like you're running the 64bit version of Ubuntu.  WINE won't compile to a 64bit executable (it has no Win64 support, so creating a 64bit wine executable would be pointless).  It looks like wineinstall is detecting this, and compiling a 32bit executable (with the -m32 flag).  This is fine, but I've never managed to get gcc-3.4 to correctly build 32bit executables, hence your "Cannot create executables" error.

I'd suggest checking out [this thread]("http://www.ubuntuforums.org/showthread.php?t=96620&highlight=wine").  It contains the details required to get the 32bit binary .deb file installed & running.

---

