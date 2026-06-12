---
title: "AllTray install error with either Debian or Ubuntu packages."
date: 2005-08-23
forum: Desktop Environments
---

### Post by jtp51 on 2005-08-23
When installing AllTray, I receive the following error message when trying to use the Debian package. I do understand that it's a dependency issue, however I was under the believe that the Debian package worked out of the box:

[FONT=Courier New]tpatrick@ubuntu51:~/Desktop$ sudo dpkg -i alltray.debian_0.60-1_i386.deb
Selecting previously deselected package alltray.
(Reading database ... 70377 files and directories currently installed.)
Unpacking alltray (from alltray.debian_0.60-1_i386.deb) ...
dpkg: dependency problems prevent configuration of alltray:
 alltray depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing alltray (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alltray[/FONT]

When I try to use the Ubuntu package, I receive this error message:

[FONT=Courier New]tpatrick@ubuntu51:~/Desktop$ sudo dpkg -i alltray.ubuntu_0.60-1_i386.deb
dpkg-deb: unexpected end of file in version number in alltray.ubuntu_0.60-1_i386.deb
dpkg: error processing alltray.ubuntu_0.60-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 alltray.ubuntu_0.60-1_i386.deb[/FONT]

Would anyone have an idea of what I need to do differently?

Thanks,

---

### Post by jebe on 2005-08-23
hi,

you can use the autopackage. just run it with "sh alltray-0.60.x86.package". (make sure you are connected to the internet)

cu jebe

---

### Post by jtp51 on 2005-08-24
jebe: Thank you. That worked, I guess I should had read more...  ;-) 

Now, I have two AllTray Icons under Applications:Accessories - however, I can fix that.

Thanks again!

---

