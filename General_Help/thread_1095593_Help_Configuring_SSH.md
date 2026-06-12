---
title: "Help Configuring SSH?"
date: 2009-03-13
forum: General Help
---

### Post by ivallejo on 2009-03-13
Hi, I'm new here.

I have two boxes, one is RedHat 9, and the other is Ubuntu     5.10.

I'm trying to set up the Ubuntu box as an SSH server, and then connect using the Redhat machine.  The Ubuntu box came without ssh, so I installed it.

Now, when I try running SSH on the ubuntu box,  (starting the service)  I get this error message.


ivallejo@isaiah-ubuntu:/etc/ssh$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.


There was another thread that I read in the archives, which suggested using ssh-keygen, which I then used:

root@isaiah-ubuntu:/etc/init.d# ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
56:de:29:88:62:54:73:06:a6:be:f1:d1:53:1d:d6:68 root@isaiah-ubuntu
root@isaiah-ubuntu:/etc/init.d# ./ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]
root@isaiah-ubuntu:/etc/init.d# su isaiah
Unknown id: isaiah
root@isaiah-ubuntu:/etc/init.d# su ivallejo
ivallejo@isaiah-ubuntu:/etc/init.d$ ./ssh start
 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.
                                                                         [fail]


Still can't start the service.  What should I try?

---

### Post by Hobgoblin on 2009-03-13
OK, first, 5.10 is old and (I think) unsupported.

How did you install ssh?  If you used the repositories then it should be running once you've installed and not need starting.

If it does need starting then you'll need to do that with sudo to give you root privileges.

i.e.
sudo /etc/init.d/ssh start

---

### Post by ivallejo on 2009-03-13
To install, I clicked on System>Administration>Synaptic Package Manager
(found on the Desktop)

Then I chose the tab for "Networking>OpenSSH Server".

I think I read somewhere that if I use a command-line tool, it will automatically configure the SSH server, is that what you're suggesting?  If so, could you suggest a command, or some resources?


Also, I did try starting the service as root:

root@isaiah-ubuntu:/etc/init.d# ./ssh start
* Starting OpenBSD Secure Shell server... [fail]

(For some reason there is just that error message and no further error messages when logged in as root)

---

### Post by ivallejo on 2009-03-13
I found the apt-get command.  I used this to uninstall my current SSH server:

root@isaiah-ubuntu:/etc/ssh# apt-get remove openssh-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  openssh-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 524kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 56671 files and directories currently installed.)
Removing openssh-server ...
 * Stopping OpenBSD Secure Shell server...                               [ ok ]



Then I reinstalled SSH server.



root@isaiah-ubuntu:/etc/ssh# apt-get install openssh-server
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  rssh
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/195kB of archives.
After unpacking 524kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 56664 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.1p1-7ubuntu4_i386.deb) ...
Setting up openssh-server (4.1p1-7ubuntu4) ...
 * Restarting OpenBSD Secure Shell server... @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/etc/ssh/ssh_host_rsa_key' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_rsa_key
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/etc/ssh/ssh_host_rsa_key' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_rsa_key
                                                                         [ ok ]




Error about permissions?  I tried setting the permissions to 600, but the error is the same.

root@isaiah-ubuntu:/etc/ssh# chmod 600 ssh_host_rsa_key
root@isaiah-ubuntu:/etc/ssh# /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]
root@isaiah-ubuntu:/etc/ssh# chmod 600 ssh_host_dsa_key
root@isaiah-ubuntu:/etc/ssh# /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]
root@isaiah-ubuntu:/etc/ssh#


Did I do something wrong?  Should I try different permissions?

---

### Post by redlinethecar on 2010-01-09
Wow same issue...  Started off with me not being able to copy files from my laptop to my desktop using scp cause it gives an error like connection refused.  Then someone told me I need to be running sshd.

Tried to run that and got an 

```
sshd re-exec requires execution with an absolute path
```

then I was told to run it different and got another error kinda like the one you got posted

```
server@server-desktop:~$ /usr/sbin/sshd
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
```

Soon though I know ill figure it out soon lol

---

### Post by redlinethecar on 2010-01-09
Just tried this:

```
ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N ""
ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N ""
ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ""

```

but still no luck im at a dead stop can't figure it out

---

### Post by jdpond on 2010-05-24
Try this (leave pass phrases empty).

This should also work if you are changing host names or other information in either the /etc/hosts or /etc/resolv.conf configurations.

```

sudo rm /etc/ssh/ssh_host_*
sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
sudo ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_rsa1_key
sudo /etc/init.d/ssh reload

```

---

