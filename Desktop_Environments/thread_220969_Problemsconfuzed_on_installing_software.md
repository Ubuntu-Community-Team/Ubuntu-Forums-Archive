---
title: "Problems/confuzed on installing software"
date: 2006-07-22
forum: Desktop Environments
---

### Post by jazzman14 on 2006-07-22
Hi,

I've tried to install many different programs that were tarballs. Once extracted, i get to the directory in terminal, when i go ./configure, it runs through a thing and says error and says to check config.log, what do I do?

---

### Post by not_yet on 2006-07-22
basically what you are doing is compiling the program

it usually goes like this

configure
make
make install

these 3 are separate steps in actually compiling the program

once done you usually run the program with ./name_of_program

if you recieved an error during the configure portion look back at the terminal output to see what the error is

post the error if you can 

cheers

---

### Post by jazzman14 on 2006-07-22
~/Desktop/clamav-0.88.3$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gawk... (cached) mawk
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by asplode on 2006-07-22
could you be more specific with the error message?

sometimes you need some development libraries...

try this

```
sudo apt-get build-dep *name of program you're compiling*
```

so, for banshee it would look like

```
sudo apt-get build-dep banshee
```

then go through the steps outlined above

```
./configure
make
sudo make install
```

---

### Post by asplode on 2006-07-22
oh, the joy of forums...

Okay, you dont have any of the build essentials installed.  There is no C compiler on your system...  So step 1 would be to get those...

```
sudo apt-get install build-essential
```

---

### Post by Omnios on 2006-07-22
> **kenascher said:**
> ~/Desktop/clamav-0.88.3$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gawk... (cached) mawk
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

 Hi the error message seems that Ubuntu can not find a C compiler. Most Error messages will tell you what you need in this case is a compiler, the same holds tru for libraries.

Anyways you might want to read these links and get build-essential.
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

