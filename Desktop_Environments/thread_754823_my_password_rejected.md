---
title: "my password rejected"
date: 2008-04-14
forum: Desktop Environments
---

### Post by tomohiro on 2008-04-14
I am feeling strange.
In the other day, I had done some operations(svn checkout etc...) on console.
 After all task is finished , I tried to type sudo. but my password rejected!
I had input same password some minutes ago , and it was accepted.

I had thourght my password changed by some causes.
but on login input , my password is accepted. so this possibility refused.

Strange facts proceed.
I had tried to change the way to start session on login input to fail safe session(not GNOME).
Mysteriously , my password was accepted on sudo . Trying to relogin and type password on sudo in this state ,  my all operations with authorization can be done.

Do you know causes and way to repair of this phenomenons?
I was forced to inconvenience  every time of l operations with authorization.


Sorry for my bad English.:(

---

### Post by bapoumba on 2008-04-14
Please run **groups** from a terminal and make sure you are in the admin group.

---

### Post by tomohiro on 2008-04-16
Thank you for your response , bapoumba.
but according to result , my account seem to  belong to admin group certainly.

---

### Post by bapoumba on 2008-04-16
It could come from several reasons then. One of them is the [/etc/sudoers]("http://linux.die.net/man/5/sudoers") file, where some permissions are setup.

Please post the complete error messages to:

```
sudo -l
sudo apt-get update
```

---

### Post by tomohiro on 2008-04-17
Yes,  It shows as follows.

yasutomo@santos:~$ sudo -l
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
sudo: 3 incorrect password attempts
yasutomo@santos:~$ sudo apt-get update
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
sudo: 3 incorrect password attempts
-----------------------------------------------

and /etc/sudoers

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by bapoumba on 2008-04-24
Sorry, I was gone for a week :)
If your user is indeed in the admin group (not adm, admin, the sudoers file is okay), and the password works when you login, make sure you have the proper keyboard layout when logged in, no capslock on (it is case sensitive), the correct language etc.

---

### Post by tomohiro on 2008-05-07
I confirmed again my user is in admin group(not adm).
And the correct string is displayed when I typed my password on a terminal.
So, keyboard settings is not unusual.

---

### Post by bapoumba on 2008-05-07
Okay.
```
bapoumba@scorpio:/etc/network$ sudo -l
[sudo] password for bapoumba: 
User bapoumba may run the following commands on this host:
    (ALL) ALL

```
What is in your /etc/hosts ?

Here is mine for ex:
```
bapoumba@scorpio:/etc/network$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	scorpio

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
scorpio is my machine name.

---

### Post by tomohiro on 2008-05-08
sudo -l
```

yasutomo@santos:~$ sudo -l
User yasutomo may run the following commands on this host:
    (ALL) ALL

```

/etc/hosts
```

yasutomo@santos:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
::1 ip6-localhost ip6-loopback
ff02::3 ip6-allhosts
ff00::0 ip6-mcastprefix
127.0.0.1 santos
ff02::2 ip6-allrouters

```

Sincerely,

---

### Post by bapoumba on 2008-05-08
[http://ubuntuforums.org/showthread.php?t=723361]("http://http://ubuntuforums.org/showthread.php?t=723361")
This is a known bug.. Add these two lines to your /etc/hosts and you should be fine :)

```
127.0.0.1	localhost
127.0.1.1	santos
```

---

### Post by tomohiro on 2008-05-14
Unfortunately, I edited /etc/hosts, but the problem is not fixed.:cry:

```

yasutomo@santos:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 santos

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
::1 ip6-localhost ip6-loopback
ff02::3 ip6-allhosts
ff00::0 ip6-mcastprefix
127.0.0.1 santos
ff02::2 ip6-allrouters
yasutomo@santos:~$ sudo a
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
[sudo] password for yasutomo:
Sorry, try again.
sudo: 3 incorrect password attempts


```

---

### Post by bapoumba on 2008-05-14
Please post:
```
cat /etc/hostname
```
They should match.
If they do match, it should work. Have you rebooted since you changed /etc/hosts ?

Did you read all the pages from the post I quoted? For some users, changing also the hostname from the network admin tools was necessary. But it messed up things for others.. [lpbug]32906[/lpbug]; [lpbug]223448[/lpbug]; [lpbug]122948[/lpbug]

---

### Post by tomohiro on 2008-05-15
/etc/hostname

```

yasutomo@santos:~$ cat /etc/hostname
santos

```

>Have you rebooted since you changed /etc/hosts ?
Yes.

I read you quoted page.
In their case, sudo says that unable to resolve host icarus-laptop.
but in my case, sudo: 3 incorrect password attempts.

I think that it occured by other causes.

---

### Post by bapoumba on 2008-05-15
Okay, would you have enabled the root account by any chance? sudo accepts the user password, not the root password.

Do you have another account on this computer to see if it is general or just with your regular user?
To make a new account, you'll have to go from recovery mode, as it needs root access. From recovery (you'll be root with a # prompt):
```
# adduser test
# adduser test admin
# reboot
```

Log in with test (you can give it any other name when creating the account) and try ```
sudo nano
``` for ex (nano is a small text editor. CTRL-X to exit). If working fine, your regular account has a problem.
I'd start with .ICEauthority and .Xauthority in your /home. You should own them.
```
bapoumba@scorpio:~$ ls -la .ICE*
-rw------- 1 bapoumba bapoumba 2093 2008-05-15 08:31 .ICEauthority
bapoumba@scorpio:~$ ls -la .Xau*
-rw------- 1 bapoumba bapoumba 118 2008-05-15 08:31 .Xauthority
```

But first see if another account has the same problem.

---

### Post by tomohiro on 2008-05-16
I created new account. but sudo refused password too.
Not only my regular account has problems.

Next, I made sure of the existence both .ICEauthority and .Xauthority.

```

yasutomo@santos:~$ ls -la .ICEauthority 
-rw------- 1 yasutomo tomohiro 318 2008-05-16 19:04 .ICEauthority
yasutomo@santos:~$ ls -la .Xauthority 
-rw------- 1 yasutomo tomohiro 100 2008-05-16 19:04 .Xauthority

```

It printed two different account names; yasutomo , tomohiro.
Is this abnormal?
yasutomo is current my accout name.
tomohiro is old name.
I had changed account name to yasutomo.

---

### Post by tomohiro on 2008-05-23
Sorry ,bapoumba.

The circumstance which I have hold deteriorated.
At the login time, my password was rejected too! ](*,
I don't know what made it .

As the result, I became to not be accepted by sudo at all the time.
Fortunately, stopping the X, I can login by CUI mode.
So I could take back-up of important data.

However , I determined re-install Ubuntu.
Sorry for many advice and your valuable time , and Thank you.

---

### Post by bapoumba on 2008-05-24
> **tomohiro said:**
> 
I had changed account name to yasutomo.
Sorry I missed that point. How did you change the account name?

---

