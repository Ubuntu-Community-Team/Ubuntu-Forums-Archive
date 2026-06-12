---
title: "VERLIHUB not compiling"
date: 2006-01-08
forum: Desktop Environments
---

### Post by tatacalu on 2006-01-08
hey there
I downloaded the source of the latest verlihub and it won't compile
the concole returns the following message:

```
root@ubuntu:~/Desktop/verlihub# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for g++... no
checking for c++... no
checking for gpp... gpp
checking for C++ compiler default output file name... b.out
checking whether the C++ compiler works... configure: error: cannot run C++ compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

any ideas ??? :(

---

### Post by tatacalu on 2006-01-08
Does anyone know if YnHUB has a linux version ?

:KS For the people that don't know that, Verlihub and YnHUB are 2 HUB-programs for Direct Connect (DC++) program.

oh, and I installed opendchub but it's very poor... and it's console-based. How can I monitor it's activities or at least turn it off ???

---

### Post by stoffepojken on 2006-01-08
You need to install build-essential:   

sudo apt-get install build-essential

---

### Post by tatacalu on 2006-01-08
./configure worked.... but...
Theese were the final lines from **make**.
```

make[2]: *** [cban.lo] Error 1
make[2]: Leaving directory `/root/Desktop/verlihub/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Desktop/verlihub'
make: *** [all] Error 2

```

I think this means that it failed, right ?
Does anybody know what might be the problem?

---

### Post by stoffepojken on 2006-01-08
If you wait 15 minutes I post all the dependecies for compiling verlihub. I did it my self a while ago

---

### Post by tatacalu on 2006-01-08
ok, i'll wait.

I checked the readme file and I have all the necessary dependencies.... but I wouldn't mind to re-check them hehehe

---

### Post by stoffepojken on 2006-01-08
This is how I did it:

sudo apt-get install mysql-server libmysqlclient10-dev libpcre3-dev geoip-bin libgeoip-dev g++-3.3

Then instead of ./configure type:

CXX=g++-3.3 ./configure

Hope It works :)

---

### Post by tatacalu on 2006-01-08
It worked!!!

Now I have a few questions:
where can I find the executable of verlihub ?

and..a.... i hope it has a graphical user interface... does it ?

---

### Post by stoffepojken on 2006-01-08
verlihub does not have a graphical interface. You configure the hub from your DC client. Have you set your self as master of the hub?

---

### Post by tatacalu on 2006-01-08
I didn't had time yet to explore verlihub.

aaa... does anyone know a good hub program for linux with a Graphical User Interface ?

---

### Post by stoffepojken on 2006-01-08
I dont think there is one. If that is what you want you should run ynhub

---

### Post by stoffepojken on 2006-01-08
To start with verlihub do like this:

First set your password in mysql:

mysqladmin -u root password **********  <--- replace the stars with a password of your choice

then type verlihub in a terminal a few lines of text comes up and stops. When it stops, close the terminal.

After that type in a terminal:

cd /usr/local/bin

Now to configure your database for verlihub type:

sudo vh_install

---

### Post by tatacalu on 2006-01-09
OK, done that.

Oh... YnHUB for Linux doesn't exist.

---

### Post by Meserias on 2007-11-24
Hi **tatacalu** do you successfully find a way to compile plugins for VerliHUB on Ubuntu 7.10 (latest release)? 
LUA, Iplog, forbid, stats, messenger ? If Yes please help me 
(I think we are both from Romania, I'm from Bucharest Romania)

:confused:

---

