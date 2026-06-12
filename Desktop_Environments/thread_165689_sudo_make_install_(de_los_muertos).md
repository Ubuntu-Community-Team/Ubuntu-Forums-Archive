---
title: "sudo make install (de los muertos)"
date: 2006-04-25
forum: Desktop Environments
---

### Post by Banter on 2006-04-25
Goal: To get my G DWL-G510 (revision b) wireless adapter to work
Problem: I cannot install ndiswrapper
Cause: "sudo make install" encounters an error

The situation:
1. I install Ubuntu Breezy Badger.

2. I immediately followed this wonderful tutorial on setting up gcc: [http://www.ubuntuforums.org/showthread.php?t=79896](http://www.ubuntuforums.org/showthread.php?t=79896)
Apparently, you need this to get ndiswrapper to install.

3. Then I attempt to follow this set of instructions on installing ndiswrapper:
> Go to the directory holding your ndiswrapper, and run: 
sudo make install

The rest of the instructions can be found here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#5_-_Installing_ndiswrapper](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#5_-_Installing_ndiswrapper)

4. I encounter this error after entering "sudo make install"

```
grant@ubuntu:~/ndiswrapper-1.14$ sudo make install
make -C driver install
make[1]: Entering directory `/home/grant/ndiswrapper-1.14/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/grant/ndiswrapper-1.14/driver'
make: *** [install] Error 2
grant@ubuntu:~/ndiswrapper-1.14$
```

Solution: can you please help me find one :)

---

### Post by ruzle0 on 2006-04-25
use synaptic to install 
linux-headers-2.6.12-9-386
and 
linux-headers-2.6.12-9

and see if it works after that

---

### Post by Banter on 2006-04-25
alright, ill give it a shot. Thanks!

---

