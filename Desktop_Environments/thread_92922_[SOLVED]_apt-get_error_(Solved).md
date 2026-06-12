---
title: "[SOLVED] apt-get error (Solved)"
date: 2005-11-20
forum: Desktop Environments
---

### Post by bss1234 on 2005-11-20
After attempting to install a printer driver package from Brother, I get an error when using apt-get for any package.

Reading package lists... Done
Building dependency tree... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.

Any suggestions on how to fix this?

---

### Post by aysiu on 2005-11-20
What's the name of the printer driver from Brother?
What's the name of your Brother printer?

---

### Post by bss1234 on 2005-11-21
Printer Driver: mfc4800lpr-1.1.2-1.i386.deb
Printer Model: Brother MFC 4800

---

### Post by aysiu on 2005-11-21
What command did you use to install the driver? Can you post the entire terminal dialogue--everything you typed and everything the terminal spits back out at you.

Is that .deb saved to your desktop? Where is it?

---

### Post by bss1234 on 2005-11-22
The file path is: /home/bss1234/Desktop/mfc4800lpr-1.1.2-1.i386.deb

The command used and output was:

bss1234@ubuntu:~$ sudo dpkg -i --force-all ./Desktop/mfc4800lpr-1.1.2-1.i386.deb
Password:
(Reading database ... 59498 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using .../mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
/var/lib/dpkg/info/mfc4800lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing ./Desktop/mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 ./Desktop/mfc4800lpr-1.1.2-1.i386.deb
bss1234@ubuntu:~$

---

### Post by aysiu on 2005-11-22
Maybe [this](http://lists.debian.org/debian-user/2005/04/msg01317.html) might help?

---

### Post by bss1234 on 2005-11-23
Link had all the info I needed. Problem solved. Thank you for all the help!!! :)

---

### Post by kodachrome64 on 2007-01-07
bss1234,

I'm having the same problem you had with the mfc4800lpr error.

What exactly did you do to resolve this.



I changed the "mfc4800lpr.postinst" file as noted and added the "exit 0" and commented out the other lines.

adam@ubuntu-macbook:/var/lib/dpkg/info$ cat mfc4800lpr.postinst
exit 0
#!/bin/sh
# ESP Package Manager v3.5.1
# /usr/local/Brother/inf/setupPrintcap MFC4800 -i USB
# /etc/init.d/lpd restart
adam@ubuntu-macbook:/var/lib/dpkg/info$

running "sudo apt-get remove --purge mfc4800lpr" still gets me the same error.

adam@ubuntu-macbook:/var/lib/dpkg/info$ sudo apt-get remove --purge mfc4800lpr
Reading package lists... Done
Building dependency tree... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
adam@ubuntu-macbook:/var/lib/dpkg/info$

What is it I'm doing wrong here?

What were the steps to the fix for you?

Thanks for any help!

---

### Post by kodachrome64 on 2007-01-07
OK,

I thnk I figured it out. I reinstalled the mfc4800lpr and then removed it.
I'm really new to this so I tried all kinds of other things and this simple solution worked for me in the end. I am now able to use Synaptic Package Manager and Update Manager with ut errors.

adam@ubuntu-macbook:/etc/init.d$ sudo dpkg -i /home/adam/Desktop/mfc4800lpr-1.1.2-1.i386.deb
(Reading database ... 78527 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using .../mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
Setting up mfc4800lpr (1.1.2-1) ...

adam@ubuntu-macbook:/etc/init.d$  sudo dpkg --purge mfc4800lpr
(Reading database ... 78526 files and directories currently installed.)
Removing mfc4800lpr ...
Purging configuration files for mfc4800lpr ...
adam@ubuntu-macbook:/etc/init.d$

---

### Post by granade on 2007-03-28
Hi,

This is my first post but not my first time on this forum. So far i have been able to solve most of my small problems from research. This however has me stomped. Im trying to get printing going on my wifes laptop using latest Ubuntu CE distro.

I downloaded mfc4800lpr-1.1.2-1.i386.deb but it the file i found has a .rpm extension. Below is my output from terminal. I followed the instructions from of this post but changed the .rpm to .deb to try to get it to run in terminal. No luck.

Thank you for any help. 


@toshiba:~$ sudo dpkg -i --force-all ./Desktop/mfc4800lpr-1.1.2-1.i386.**deb**[changed from .rpm to .deb
dpkg-deb: `./Desktop/mfc4800lpr-1.1.2-1.i386.deb' is not a debian format archive
dpkg: error processing ./Desktop/mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 ./Desktop/mfc4800lpr-1.1.2-1.i386.deb

---

### Post by Gloppie on 2007-12-18
Hi all,
I tried to install the mfc4800lpr and cups driver from Brother on Gutsy Gibbon.
Never got it to print, got rid of it, but my Synaptic is a mess now.
Cups is not the issue, MFC4800lpr is.
I have tried 
[http://lists.debian.org/debian-user/2005/04/msg01498.html](http://lists.debian.org/debian-user/2005/04/msg01498.html)
[http://ubuntuforums.org/showthread.php?t=84676](http://ubuntuforums.org/showthread.php?t=84676)
and this thread too.
I mixed and match trying to get this resolved and made it worse it seems.

here is some info

in terminal:
gloppie@ksla-Linux-Ym:~$ sudo apt-get remove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
Synaptic:
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
then exits

/var/lib/dpkg/info/mfc4800lpr.prerm contains
exit 0
#!/bin/sh
# ESP Package Manager v3.5.1
#/usr/local/Brother/inf/setupPrintcap MFC4800 -e

/var/lib/dpkg/info/mfc4800lpr.postinst contains
exit 0
#!/bin/sh
# ESP Package Manager v3.5.1
#/usr/local/Brother/inf/setupPrintcap MFC4800 -i USB 
#/etc/init.d/lpd restart

/var/lib/dpkg/info/mfc4800lpr.postrm
exit 0
#!/bin/sh
# ESP Package Manager v3.5.1
#/etc/init.d/lpd restart

I have edited all 3 files. I still have the package and copied it to /desktop /home /documents to no avail.

This is quite annoying, I can not get updates anymore. I was so proud of myself, Linuxing away and all. I have been trying on and off since the 486 days to switch to Linux, Mandrake 7, Debian, Suse 9 or earlier I can't remember.
Not only do I need help fixing this, I want to understand WHY and how it broke.
I saw in past post "ho, what the hell is this package doing, good that DPKG did not allow" 
I could not figure why it was an issue. I am still a newbie.
Is there any good "history of where the Linux folders are and do" anywhere on the web?
Anywho..I hope I will get help from someone, thank you in advance !

Yves

---

### Post by Gloppie on 2007-12-18
Well, I tried APtitude, and here is the result of a purge on the offender.

dpkg: error processing mfc4800lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc4800lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

but I am not sure I can re-install it, or how.

Learning continues....:confused:

---

### Post by Gloppie on 2007-12-18
Well, this was solved by Question #4838 in Ubuntu
thanks to 
Greg McKay and ramjet_1953 for the fix !!

---

