---
title: "Help compiling an app"
date: 2009-01-19
forum: General Help
---

### Post by NeonBible on 2009-01-19
I am trying to install ncmpc++ - [http://unkart.ovh.org/ncmpcpp/download.php](http://unkart.ovh.org/ncmpcpp/download.php)

I am following the instructions for the git repo.

I get to the point where I run ./configure and I get the following output.  Also do I need to specify any options here?

name@computer:~/ncmpcpp/ncmpcpp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Does it mean I'm missing all with a 'no' next to it?

---

### Post by adult swim on 2009-01-19
try running ```
sudo apt-get install build-essential
``` and then cd back to the directory you were in and ./configure again

---

### Post by hal8000 on 2009-01-19
> **NeonBible said:**
> I am trying to install ncmpc++ - [http://unkart.ovh.org/ncmpcpp/download.php](http://unkart.ovh.org/ncmpcpp/download.php)

I am following the instructions for the git repo.

I get to the point where I run ./configure and I get the following output.  Also do I need to specify any options here?

name@computer:~/ncmpcpp/ncmpcpp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Does it mean I'm missing all with a 'no' next to it?


Yes, it means that either the package is not installed or cannot be found.
You also need to look at the file config.log for more details.
You wont necessarily have to install packages installing gcc means that you you can the gnu gcc compiler instead of CC for example. The best way is to read the help or install file that comes with a program.
Also bear in mind that adding software from non-repo sources has to be removed manually and sometimes can cause something else to break.
Hope that helps.

---

### Post by NeonBible on 2009-01-19
> **adult swim said:**
> try running ```
sudo apt-get install build-essential
``` and then cd back to the directory you were in and ./configure again

This one worked! thanks.

---

