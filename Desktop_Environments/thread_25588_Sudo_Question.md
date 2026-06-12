---
title: "Sudo Question"
date: 2005-04-10
forum: Desktop Environments
---

### Post by sinbad782 on 2005-04-10
Hi all, 
   I'd like to install Ubuntu on a couple of older machines (P2 233/300Mhz boxes) that I have set up with Debian Unstable at present and that are used as public terminals in a student residence. Generally these have a single user account plus a root account for my admin. I usually administer these machines remotely using SSH. 

If I install Ubuntu, I'd rather not have the students messing around installing stuff using sudo and so the question is, how do I prevent the user account that I set up for the student's general use being a sudoer?

Is it sufficient to set the root password and then simply edit out the references to this account in the file /etc/sudo or is there something deeper that needs to happen?

Any comments welcome!

PJS

---

### Post by miklov on 2005-04-10
I believe the first account that you set up (during installation) will be a member of the sudo group.

When you come to adding the user accounts for the students to use, check that they are not members of the sudo group; using System --> Administration --> Users and Groups.

You will probably have to make sure that the 'Show all users and groups' tick box is selected. Then click on the Groups tab and find the sudo group and click the Properties button and check the members.

---

### Post by iamkmaniam on 2005-05-25
You can also enable the wheel group and add yourself to it. Only users in the wheel group have access to the su  command. Hope this helps.

---

### Post by Mez on 2005-05-25
Hey there.

This is pretty simple.

on a default install, sudo cna only be used by those in the admin group

```
 /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

I would suggest, to keep things secure is to use the System --> Administration --> Users and Groups. to create a new group, and add it to the "admin" group

Then, login to that, and remove the old user from the admin group

This old user can now no longer use sudo, whereas your new user can, and your system is still secure!

---

