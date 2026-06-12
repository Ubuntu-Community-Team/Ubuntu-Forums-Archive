---
title: "C Compiler/Application Location"
date: 2005-12-08
forum: Desktop Environments
---

### Post by nkingcade on 2005-12-08
All,

I have two questions:

1. I have installed the gcc compiler using the synaptic. How do I add the application to my $PATH so it can be found by the ./configure process?

2. When I compile and application in the usr/src folder, where does the executable reside? In this case NMAP 3.95? 

Thanks,

Neal

---

### Post by taurus on 2005-12-08
Both /bin & /usr/bin should be in your path so no need to add them again.  Otherwise, you can add these two lines to your ~/.bashrc

PATH=$PATH:{wherever you want to point to}:/usr/local/bin
export PATH

Normally, if you want to compile something from source, you need to run
./configure
make
sudo make install

Don't forget you need to be root to run "make install" since it will install the binary of the program, usually, in /usr/local/bin unless you specify somewhere else in .configure.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=nkingcade]
1. I have installed the gcc compiler using the synaptic. How do I add the application to my $PATH so it can be found by the ./configure process?
[/QUOTE]
If you installed the "build-essentials" package which includes gcc, it should be in /usr/bin.  /usr/bin should already be in your PATH.

---

### Post by nkingcade on 2005-12-08
Thanks, Everyone for the rapid response.

Neal

---

### Post by nkingcade on 2005-12-09
New Question:

The "build-essentionals is not in the /usr/bin directory. If I download or install the compiler, how do I get the machine to know where to find it when needed? Also, is the ./configure function part of the compiler? I understand it is just a check, where does it originate?

Neal

---

### Post by taurus on 2005-12-09
Build-essential is not one package.  It's a combination of packages that you need to install on your system if you plan to build something from source...  Therefore, there is no such thing as build-essential command that you can run with.  

./configure is not part of the compiler; instead, it's part of the program that you want to build.  When you run ./configure from a prompt, it will look for all the programs/libraries that it needs and creates a Makefile (or Makefiles) for it.  That's why most of the time if you want to build something from source, you need to run

./configure
make
make install (need to be root to run this command...)

---

### Post by nkingcade on 2005-12-10
Thanks Taurus.
I kind of thought that. 
Thanks for the verification.

---

