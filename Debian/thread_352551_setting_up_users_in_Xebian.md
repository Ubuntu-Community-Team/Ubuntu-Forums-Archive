---
title: "setting up users in Xebian"
date: 2007-02-03
forum: Debian
---

### Post by foxy123 on 2007-02-03
I have recently installed Xebian on xbox and it runs nicely. The problem is that it lacks a lot of gui admin tools I get used to on Ubuntu. For example I cannot figure out how to give certain privileges to users. On Ubuntu I can run
```
users-admin
```
and access users and groups and grant admin privileges to the users. But I cannot find this command on Xebian. Is is a part of some package? In general how to use command line to do the same  things?

---

### Post by AgenT on 2007-02-04
It is much easier to figure out than you may think. For example, to add user use this command: useradd
To delete user: userdel
To modify user: usermod
To show users: users
To show groups: groups
To add a group: groupadd
Just use the man page for useradd and groupadd which will not only show you how to use those commands but also point you to other related ones.
[http://learnlinux.tsf.org.za/courses/build/sys-admin/ch05.html](http://learnlinux.tsf.org.za/courses/build/sys-admin/ch05.html)
[http://www.debianhelp.co.uk/userandgroup.htm](http://www.debianhelp.co.uk/userandgroup.htm)

And when you have such problems, you should look into reading Debian documentation. It is better than Ubuntu's (which is mostly a random copy/paste of Debian docs). Gentoo documentation is also good.

---

