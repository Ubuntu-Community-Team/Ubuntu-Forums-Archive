---
title: "Problem with Debians and RPMs"
date: 2006-01-15
forum: General Help
---

### Post by zortox12 on 2006-01-15
Oi it works fine hen i install debs but i accidently installed "rpm" so i dont hafto convert but it needs a dependdency so i try to convert the dependincy to a deb but it pops this error message:root@ubuntu:/home/zortox12/Desktop# alien rpm-libs-4.4.2-13.i386.rpm
sh: rpm: command not found
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} rpm-libs-4.4.2-13.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
root@ubuntu:/home/zortox12/Desktop#

---

### Post by apricot on 2006-01-15
Also experiencing problems with converting .rpm to .deb,
this is what it turns back:

~$ sudo alien bjfilter-common-2.50-2.i386.rpm
Password:
xargs: chmod: terminated by signal 4
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488, <GETPERMS> line 4.
Package build failed. Here's the log:
find: bjfilter-common-2.50: No such file or directory

Please, help.

---

### Post by RAOF on 2006-01-15
The answer to both your questions is another question: 
"What program are you trying to install?"
This is in a series of questions:
"Why do you want this program? (as in, what does it do?)"
"Why aren't you using apt-get/synaptic?"

The alien program should always be a last-resort.  It doesn't always work (as you've found), and when it does, the packages it produces don't always work.  For almost everything you shouldn't need to deal with .deb or .rpm files - use synaptic or apt-get.  Check [this page out]("http://www.psychocats.net/linux/installingsoftware.php") (gratefully taken from aysiu's sig) for information about installing stuff in Ubuntu the easy way.

---

