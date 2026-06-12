---
title: "Converting softwares to ubuntu"
date: 2006-08-16
forum: Desktop Environments
---

### Post by thilina on 2006-08-16
Now can I convert Fedora core installation files(*.i386.rpm) to ubuntu type??

---

### Post by kaffelars on 2006-08-16
Yes, you can with the **alien**-application available in Synaptic.
You can then convert an RPM using this command:
**sudo alien -d package.rpm**, and then install the deb with **sudo dpkg -i package.deb**

The converted packages don't *always* work, however, but it's worth a try!

---

### Post by 505 on 2006-08-16
That program is called 'alien'. It's not installed by default. 

Type 'sudo apt-get install alien' to install it

Type 'sudo alien *.i386.rpm' to convert the files

Type 'sudo dpkg -i *.deb' to install them.

---

### Post by thilina on 2006-08-16
I have to get it from  the net ,isnt it??
My dial up connection is not working,shit

---

### Post by dmacdonald95 on 2006-08-16
Quick message to tell you not to swear, if you could manage, thanks :)

---

### Post by kaffelars on 2006-08-17
I think you have to get it from the net, yes. You could always download the package on another computer, but if I remember correctly it has a few dependencies that you need as well.

You should check your CD to be sure, though :)

---

