---
title: "errors on chess install"
date: 2022-05-06
forum: Gaming &amp; Leisure
---

### Post by cmcanulty on 2022-05-06
I am trying to install scidb chess which worked fine in 20.04 but fails in 22.o4. Here is the error code and a screenshot showing I have at least the required version install of gcc. Please help me fix this.
```

cmcanulty@DellInspiron-660s:~/scidb-code-r1531-trunk$ ./configure
configure: Makefile configuration program for Scidb
    Tcl/Tk version: 8.6
    Your operating system is: Linux 5.15.0-27-generic
                 Distributor: Ubuntu
                    Revision: 22.04
                     Version: 22.04 LTS (Jammy Jellyfish)
    Checking if your system has gcc installed: yes,
    but existing gcc version 11.2 is too old.

    The required version is 3.4 and higher.
cmcanulty@DellInspiron-660s:~/scidb-code-r1531-trunk$ 

```

[ATTACH=CONFIG]290406[/ATTACH]

---

### Post by octawizard43 on 2022-05-06
I maybe have a solution i have started with Ubuntu about an year ago but joined the forum today and that is why i know many things. So i can tell you im not an expert but i think when i read the error code it says that existing GCC is too old and the required version is 3.4 and higher. It's weird but i think you need to update it. The weird that you say you have GCC 11.2 and its too old. The error code said the required GCC version is 3.4 which is lower so basically no update a downgrade. But when i check the latest version of GCC its version 12.1. So maybe an update or downgrade i don't know. But i can say this try to update your programs first with this command in the terminal (sudo apt update) Then after that (sudo apt upgrade) You can also update the whole operating system with the command in the terminal (sudo apt dist-upgrade) This command sudo apt dist-upgrade can be good to combine with sudo apt update and sudo apt-upgrade. If it is still problem even when you have updated your applications and system maybe it is a compability issue like if it was made for a really old Ubuntu version. So old Ubuntu version that you must downgrade the system but i don't think that's the problem but again im not an expert. I suggest you update GCC with updating commands in terminal first.

---

### Post by octawizard43 on 2022-05-06
Quick note if you cant update maybe reinstalling gcc can help with (sudo apt remove gcc --purge) then after that (sudo apt autoremove -y) Then reinstalling the chess game and type in terminal (sudo apt autoremove -y) Im not an expert so if it dosen't work maybe someone else will fix it.

---

### Post by cmcanulty on 2022-05-08
OK I have made a lot of progress by doing the following:
OK update I used this web site to install and older gcc. The oldest one that worked for scidb ./configure was gcc 9
[https://www.linuxcapable.com/how-to-install-gcc-compiler-build-essential-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-gcc-compiler-build-essential-on-ubuntu-22-04-lts/)
so I did the  code:

```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 60 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9

```

then I did tcl fix as follows
sudo apt install tcl-dev

then I get a new error:
ys_info.cpp:30:11: fatal error: sys/sysctl.h: No such file or directory
I tried installing sysconftoolwith no luck
so now ./configure runs and make runs most of the way and then fails on 

```
sys_info.cpp:30:11: fatal error: sys/sysctl.h: No such file or directory
```

searching has given me no solution on how to get that file or app

---

### Post by #&amp;thj^% on 2022-05-08
use the" --enable-multiarch" option
more here: [https://gcc.gnu.org/wiki/InstallingGCC](https://gcc.gnu.org/wiki/InstallingGCC)

---

### Post by jawilljr2 on 2022-05-08
cmcanulty,  [You Need to read this thread.](https://sourceforge.net/p/scidb/bugs/210/)

---

### Post by cmcanulty on 2022-05-19
Here is my finished scidb chess install tutorial

[ATTACH]290524[/ATTACH]

---

