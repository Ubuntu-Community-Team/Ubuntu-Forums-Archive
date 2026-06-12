---
title: "x11vnc"
date: 2006-10-03
forum: Desktop Environments
---

### Post by ZERO_SHIFT on 2006-10-03
Hi

Tried to install x11vnc and got this error while <./configure>.

A working X window system build environment is required to build x11vnc.
Make sure any required X development packages are installed.  If they are
installed in non-standard locations, one can use the --x-includes=DIR
and --x-libraries=DIR configure options or set the CPPFLAGS and LDFLAGS
environment variables to indicate where the X window system header files
and libraries may be found.  On 64+32 bit machines you may need to point
to lib64 or lib32 directories to pick up the correct word size.

Any ideas?? What should I do??

thanks in advance (tia)

---

### Post by mitch.c on 2006-10-03
> **ZERO_SHIFT said:**
> Hi

Tried to install x11vnc and got this error while <./configure>.

A working X window system build environment is required to build x11vnc.
Make sure any required X development packages are installed.  If they are
installed in non-standard locations, one can use the --x-includes=DIR
and --x-libraries=DIR configure options or set the CPPFLAGS and LDFLAGS
environment variables to indicate where the X window system header files
and libraries may be found.  On 64+32 bit machines you may need to point
to lib64 or lib32 directories to pick up the correct word size.

Any ideas?? What should I do??

thanks in advance (tia)
Any reason your not using the x11vnc package?

I'm going to guess you need libx11-dev at the very least. You might try checking the output of:
```
apt-cache showsrc x11vnc
```
... to determine the dependencies.

Or even installing the build-depends:
```
sudo apt-get build-dep x11vnc
```

Let me know if that helps. Good Luck!

---

### Post by ZERO_SHIFT on 2006-10-04
Tried it but all I got was this:

zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$ apt-cache showsrc x11vnc
zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$ sudo apt-get build-dep x11vnc
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for libvncserver
zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$     

Any ideas??

---

### Post by mitch.c on 2006-10-04
> **ZERO_SHIFT said:**
> Tried it but all I got was this:

zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$ apt-cache showsrc x11vnc
zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$ sudo apt-get build-dep x11vnc
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for libvncserver
zaidammar@HAL-01:~/Applications/x11vnc-0.8.2$
Do you have the universe repository enabled? I just ran this and had absolutely no trouble. I'm on Dapper with main restricted universe and multiverse repositories enabled.

You might try:
```
sudo apt-get install libvncserver-dev
sudo apt-get build-dep x11vnc
```

It should work.

---

### Post by ZERO_SHIFT on 2006-10-04
This is what happened:-

zaidammar@HAL-01:~$ sudo apt-get install libvncserver-dev
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libvncserver-dev
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 154kB of archives.
After unpacking 516kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libvncserver-dev 0.7.1-5 [154kB]
Fetched 154kB in 20s (7499B/s)
Selecting previously deselected package libvncserver-dev.
(Reading database ... 107369 files and directories currently installed.)
Unpacking libvncserver-dev (from .../libvncserver-dev_0.7.1-5_i386.deb) ...
Setting up libvncserver-dev (0.7.1-5) ...
zaidammar@HAL-01:~$ apt-cache showsrc x11vnc
zaidammar@HAL-01:~$ sudo apt-get build-dep x11vnc
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for libvncserver

Whats going on?? Why isn't it working?

I am using Dapper too.

P.S. How do insert the <Code:> box in the forum??

tia

---

