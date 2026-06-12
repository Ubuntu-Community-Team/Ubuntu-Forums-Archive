---
title: "Install Logitech mx 518"
date: 2005-12-02
forum: Desktop Environments
---

### Post by ghepardo on 2005-12-02
I am trying to install this mouse on ubuntu 5.10, to get it work at 1600dpi. TO do this I downloaded logitech applet, but I have a problem when I try to install.

To install it I do the ./configure command, but it does not create the "make" file. Why? This is the output:

manu@ubuntu:~/logitech_applet-0.4test1$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for usb_init in -lusb... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
manu@ubuntu:~/logitech_applet-0.4test1$ sudo ./make
sudo: ./make: command not found
manu@ubuntu:~/logitech_applet-0.4test1$


What can I do?

I hope someone helps me.

Thank you all, replyers ^^.

---

### Post by teaker1s on 2005-12-02
you need Build-essential and also I installed checkinstall as the version needs setting
eg
./configure
make
sudo checkinstall

now onto the next issue when it's installed I failed to get it to run and it doesn't create a log file
you may me better searching multimedia in wilki and using that as I did for any multimedia codes + currently it's widely known on the internet that certain logitech mice don't give output on tilt left/right so you can't do much with them

---

### Post by ghepardo on 2005-12-02
I downloaded both build essentials and checkinstall but I cant get this software to install T_T

---

### Post by teaker1s on 2005-12-02
two problems I had was name and version I used logitech and 0.4.1 as version

---

### Post by ghepardo on 2005-12-03
Thank you, I installed it. Do you know how can I now enable 1600dpi resolution, plus the other mouse buttons ?

---

