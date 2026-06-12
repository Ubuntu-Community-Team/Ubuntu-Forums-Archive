---
title: "can not login even with correct password"
date: 2013-05-16
forum: Desktop Environments
---

### Post by chillfill on 2013-05-16
Hi, I am using UBUNTU 12.04.
I have been looking around and trying different solutions for the problem but none of them seem to work so please help me.
I was configuring APACHE ANT environment variables so i opened ~/.profile and  wrote down following lines of code
 ```
JAVA_HOME="BLA/BLA/BLA"
ANT_HOME= "/BLA/BLA/BLA"
PATH ="/BLA/BLA/BLA"

```
to confirm that it had installed i executed the command
```
ant -version
```
there was an error, according to some forums the system had to be restarted.
After system restart, when i entered correct password a black screen showed for few seconds and then Login screen was showed again. 
If I log-in as root user I can perform all the tasks but I have no access to that account for which I modified the ~/.profile . 
from root user when I execute this command
```
ant -version
```
it shows correct version which means that installation is correct.

I have tried deleting and creating new user from root but it does not work.
I have tried to run several commands in the recovery console which i get by pressing CTRL+ALT+F1 as proposed in different question on the forum but most of them do not run and error is shown that```
 SU
``` or```
 SUDO
``` command is not available...

pleases tell how can I solve this issue..? 
if you know any way that i can use to revert back to original ~/.profile  file or undo the changes i made please do tell. thanks

---

### Post by dino99 on 2013-05-16
[http://askubuntu.com/questions/55488/install-upgrade-to-apache-ant-1-8-2](http://askubuntu.com/questions/55488/install-upgrade-to-apache-ant-1-8-2)

the easiest way is to create a new user, so creating a new .profile
[https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html)

---

### Post by midnightramen on 2013-05-17
one thing to keep in mind is that 'su' and 'sudo' are lowercase commands, not uppercase. To change users, I have usually used 'sudo su - <username>, although I have not tried it as root. I usually login as a more restricted user, and only use 'sudo' when necessary.

There is no automatic backup of the .profile file, although you may be able to retrieve the default one at /etc/skel/.profile.

---

