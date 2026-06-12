---
title: "where you think is the problem below...? I am sure I typed correct admin root pass..."
date: 2017-03-03
forum: Desktop Environments
---

### Post by lsepolis123 on 2017-03-03
ubuntu 16.04

where you think is the problem below...? I am sure I typed correct admin root pass....

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


x@ubuntu:~$ uname -r
4.4.0-31-generic
x@ubuntu:~$ sudo apt-get update
[sudo] password for x: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
AppStream cache update completed, but some metadata was ignored due to errors.
[COLOR=#ff0000]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)[/COLOR]
[COLOR=#ff0000]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]
x@ubuntu:~$ su -
Password: 
[COLOR=#ff0000]su: Authentication failure[/COLOR]
x@ubuntu:~$ su
Password: 
su: Authentication failure
x@ubuntu:~$ sudo apt-get remove docker docker-engine
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
x@ubuntu:~$

---

### Post by howefield on 2017-03-03
> **lsepolis123 said:**
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Generally means that you have more than one package manager running simultaneously.

Close down all instances of apt, eg software centre, synaptic, update manager, ect ?

---

### Post by &amp;KyT$0P# on 2017-03-03
> **howefield said:**
> Generally means that you have more than one package manager running simultaneously.

Close down all instances of apt, eg software centre, synaptic, update manager, ect ?
Also make sure unattended-upgrades is not running.

> **lsepolis123 said:**
> 
x@ubuntu:~$ su -
Password: 
[COLOR=#ff0000]su: Authentication failure[/COLOR]
x@ubuntu:~$ su
Password: 
su: Authentication failure
This error is because the root password is locked and disabled in Ubuntu.  [FONT=Courier New]sudo su[/FONT] should work.

---

### Post by lsepolis123 on 2017-03-06
I want use apt get to install docker,.. how shut down others?

---

### Post by QIII on 2017-03-06
Hello!

The typical case is that one has a GUI package manager open, like synaptic or the Software Center (or whatever it is called these days.)

Close those if you have any open.

---

