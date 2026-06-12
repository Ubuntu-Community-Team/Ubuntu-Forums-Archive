---
title: "Dillo install failed"
date: 2008-12-10
forum: General Help
---

### Post by rioguia on 2008-12-10
I failed in trying to install Dillo using the fltk-2.0.x-r6525 and dillo-2.  Thanks in
advance for any help you might suggest.

Step 1:
Removed old Dillo 

    * apt-get remove dillo


Step 2:

Installed the packages "build-essential", "auto-apt", and "checkinstall".

    * apt-get install build-essential auto-apt checkinstall


Step 3:

Set up auto-apt by running the following commands:
Code:

    * auto-apt update
    * auto-apt updatedb
    * auto-apt update-local

Step 4:

Down loaded the fltk2 source tarball.

Step 5:

Extracted the fltk source tarball and go into the fltk-2.0.x-r6525
directory and executed the following commands:

sudo auto-apt run ./configure
sudo make
sudo checkinstall

Step 6:

Down loaded the dillo deb tarball and ran ./configure.
[[The only error message received was for the libssl-dev.  I could not
install this because I could not get the verifcation on the package to
work.  Since this package is optional I doubt this was the problem.]]

Step 7:

I ran make and received an error message.  Here is the output of make check

[[/usr/bin/ld: cannot find -lfltk2_images
collect2: ld returned 1 exit status
make[2]: *** [dillo] Error 1
make[2]: Leaving directory `/home/myusername/dillo-2.0/src'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/myusername/dillo-2.0/src'
make: *** [check-recursive] Error 1

---

### Post by aysiu on 2008-12-10
Maybe instead of compiling from source, you can try installing the Debian Lenny .deb file?
[http://misc.andi.de1.cc/dillo/dillo_2.0-1lenny_i386.deb](http://misc.andi.de1.cc/dillo/dillo_2.0-1lenny_i386.deb)

---

### Post by mkvnmtr on 2008-12-10
Dillo is in my repositories. I believe you can just type apt-get install dillo and don't have to go though all that. Unless you are just doing it for practice, then don't pay any attention to me.

---

### Post by aysiu on 2008-12-10
> **mkvnmtr said:**
> Dillo is in my repositories. I believe you can just type apt-get install dillo and don't have to go though all that. Unless you are just doing it for practice, then don't pay any attention to me.
I think the idea is to get a slightly newer version of Dillo installed.

---

### Post by rioguia on 2008-12-11
Thanks for the responses.   I did have the old version of Dillo installed previously.  I am trying to install the latest Dillo.  I understand that its been ported to the new Fast Light Toolkit (FLTK) Version.2 and its supposed to be quite an improvement.  I tried various packages for the latest Dillo with various install methods but they all failed validation (I'll have to check my notes at home to see if I used your packages).  From my research, I have a vague sense that the issue may relate to GCC6 dynamic linking not matching up to Dillo's static build (that might explain why the FLTK install and the Dillo configure all run without errors but the Dillo install fails).

---

### Post by rioguia on 2008-12-11
I get an error when I attempted install aysiu's .deb (Error: Dependency is not satisfiable: libc6.).

---

### Post by aysiu on 2008-12-11
What version of Ubuntu are you using?

I tried the Lenny .deb file on a fresh Ubuntu 8.10 (Intrepid) installation, and it worked just fine, and there weren't any unsatisfied dependencies.

---

### Post by rioguia on 2008-12-11
I am using 8.04 but since neither the compile nor the .deb package will work I have to think its specific to my machine.

In case I try this again in the future, could you tell me the version of your library?  Mine is as follows:

:~/dillo-2.0$ sudo dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libc6          2.6.1-1ubuntu1 GNU C Library: Shared libraries

Thanks.

---

### Post by aysiu on 2008-12-11
It looks as if Intrepid is 2.8:
[http://packages.ubuntu.com/intrepid/libc6](http://packages.ubuntu.com/intrepid/libc6)

---

