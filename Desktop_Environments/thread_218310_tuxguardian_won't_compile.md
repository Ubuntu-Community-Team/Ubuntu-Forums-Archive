---
title: "tuxguardian won't compile"
date: 2006-07-18
forum: Desktop Environments
---

### Post by stinkball on 2006-07-18
Here is my output from trying to compile tuxguardian:


```

stinkball@ubuntu-desktop:/usr/src/tuxguardian/tuxguardian-0.5$ sudo make


Compiling and installing the frontend
------------------------------------------------
make[1]: Entering directory `/usr/src/tuxguardian/tuxguardian-0.5/frontend'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `/usr/src/tuxguardian/tuxguardian-0.5/frontend'


Compiling the daemon
------------------------------------------------
make[1]: Entering directory `/usr/src/tuxguardian/tuxguardian-0.5/daemon'
gcc -pthread daemon.c pblhash.c pbl.c md5.c -o tg-daemon
daemon.c: In function ‘main’:
daemon.c:1286: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
make[1]: Leaving directory `/usr/src/tuxguardian/tuxguardian-0.5/daemon'


Installing the daemon
------------------------------------------------
make[1]: Entering directory `/usr/src/tuxguardian/tuxguardian-0.5/daemon'
Done.
make[1]: Leaving directory `/usr/src/tuxguardian/tuxguardian-0.5/daemon'


Compiling the module
------------------------------------------------
make[1]: Entering directory `/usr/src/tuxguardian/tuxguardian-0.5/module'
make -C /lib/modules/2.6.15-26-386/build/ SUBDIRS=/usr/src/tuxguardian/tuxguardian-0.5/module modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-386/build/: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/tuxguardian/tuxguardian-0.5/module'
make: *** [all] Error 2

```

documentation can be found here: [http://tuxguardian.sourceforge.net/documentation.php](http://tuxguardian.sourceforge.net/documentation.php)

I believe I have everything installed I need to.  I'm just lost on how to interpret some of these errors.

---

### Post by moma on 2006-07-18
You must install Linux source (or header files) for the actual kernel version. Do:

What's your kernel?
$ uname -r
2.6.15-26-386  <-- Obviously this.

$ sudo apt-get update

Search for kernel source
$ apt-cache search $(uname -r)
....

Install found kernel source package
$ sudo apt-get install linux-headers-2.6.x-y-z
-----------------------

You'll will also need (for the GUI).
    * qt3-dev-tools
    * libqt3-headers
    * libqt3-mt-dev
    * gcc4 (depending on your system) <-- Part of "build-essential" package.

Do 
apt-cache search 
and apt-get them all.

// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by stinkball on 2006-07-18
I already have all of those installed and my kernel version is: 2.6.15-26-386

---

### Post by moma on 2006-07-18
You are running Dapper Drake (ubuntu 6.06).

Do you have /lib/modules/2.6.15-26-386/ and /lib/modules/2.6.15-26-386/build/ directories?

Check 
$ ls -l /lib/modules/2.6.15-26-386/

Do:
$ sudo apt-get install --reinstall linux-headers-$(uname -r) 

$ sudo apt-get install --reinstall linux-image-$(uname -r) 

$ sudo apt-get install --reinstall linux-restricted-modules-$(uname -r)
---

In my case the /lib/modules/2.6.15-23-k7/build is a symbolic link to /usr/src where the source resides.
$ ls -l  /lib/modules/$(uname -r)/build
lrwxrwxrwx 1 root root 35 2006-05-29 13:53 /lib/modules/2.6.15-23-k7/build -> /usr/src/linux-headers-2.6.15-23-k7

---

### Post by stinkball on 2006-07-18
I think that did it. thanks, moma :-D

---

