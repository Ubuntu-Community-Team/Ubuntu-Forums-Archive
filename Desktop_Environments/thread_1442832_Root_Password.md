---
title: "Root Password"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Datamac on 2010-03-30
How to login as root?  During successful installation no prompt for creating root user or password was made.  How can I login as root on a 8.04 Hardy Heron desktop O/S?

---

### Post by sisco311 on 2010-03-30
The first user created during the installation is an Administrative user. Admin users are allowed to run applications as root without having to know the root password. 

When needed GUI applications will prompt you for your user password. In the CLI you can use sudo/gksu to run an application as root.

This explains it better:
[uhelp]community/RootSudo[/uhelp]

---

### Post by ravikalsi27 on 2010-03-30
if u wana login as a root in terminal just type
sudo su
it will ask password of root,hit enter
u will login as root in terminal

more ever if u wana login as a root in GUI ........it is possible but it will effect u r system and crash occurs...................simple use nautilas script (OPEN AS ROOT)

---

### Post by jrssystemsnet on 2010-03-30
> **ravikalsi27 said:**
> if u wana login as a root in terminal just type
sudo su

I used to do that, until I read the manpage for sudo and discovered the **-s** argument (open a root shell).

Not that it matters really for any reason that I can see; **sudo su** will work fine - just thought you might want to know. :)

---

### Post by sisco311 on 2010-03-30
> **jrssystemsnet said:**
> I used to do that, until I read the manpage for sudo and discovered the **-s** argument (open a root shell).

Not that it matters really for any reason that I can see; **sudo su** will work fine - just thought you might want to know. :)

Or even better, use: **sudo -i**

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see : [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")


**sudo su** is a freaky combination of commands. Two setuid root commands to start a root shell...uh... What's next?  pkexec sudo su -c "ping localhost"? :)

---

### Post by thomasaaron on 2010-04-16
Here's some good community documentation on understanding root in Ubuntu...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

