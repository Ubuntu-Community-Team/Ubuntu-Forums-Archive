---
title: "Errors"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-13
Hi

I need to reinstall sanaptic and update maniger and I am getting this error when I try!!  Help

> jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared is not in the sudoers file. This incident will be reported.
jared@jared-desktop:~$

How can I fix this error????  

Thanks for the help!!

---

### Post by llamakc on 2006-09-13
It isn't an error. It is warning you that user 'jared' doesn't have sudo rights.

Is 'jared' the FIRST user you created when you installed Ubuntu? Did you install Ubuntu, Kubuntu, or Xubuntu? Was this a clean disk with no leftovers from an earlier installation?

Meanwhile, you need to login as the user you created when installing [user1] and go to SYSTEM | ADMINISTRATION | USERS AND GROUPS and add user jared to the 'administrative tasks' group on the last tab named 'user privileges' after choosing 'properties' for the user you want to add.

---

### Post by Magiczero on 2006-09-13
Yes Jared is the username I used when I installed.  I am using Ubuntu..  Jared is the only user on the system

---

