---
title: "VMWare: weird problem"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Tergemble on 2006-06-22
hey all, 
A few hours ago I installed VMW Workstation for the first time ans it ran very well Win XP as guest.  After a reboot, VMWare didn't play anymore, it gave this error:

> Unable to change virtual machine power state: Failed to connect to peer process.

I get the same message as root...

Thanks, Tergemble

---

### Post by Tergemble on 2006-06-22
this worked:
[http://ftp.cvut.cz/vmware/vmware-any-any-update101.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update101.tar.gz)

(./runme.pl)

close please!

---

### Post by rasdol on 2007-07-16
I have the same error with vmware workstation 6. Is anybody have solution? I run vmware  with sudo.

May be this is a solution
[http://ubuntuforums.org/showthread.php?t=432152&highlight=vmware+connect+to+peer&page=2](http://ubuntuforums.org/showthread.php?t=432152&highlight=vmware+connect+to+peer&page=2)

---

### Post by sailorxyz on 2007-07-18
Hi, 

Dont know if you are using a 64 bit machine but I am and I had the same problem.

It looks like feisty-amd64 does not install some 32-bit libraries by default as you are expected to be running a 64-bit OS.

Nevertheless, if you try to power up a 32-bit virtual machine (not tried with a 64-bit VM) some libraries appear to be missing.

The solution is to install the 32-bit libraries required by Ubuntu to recognize the 32-bit operating system. Proceed as follows:

sudo apt-get install ia32-libs

No need to reboot nor to log out.

The 32-bit virtual machine should now power up.

Regards

---

