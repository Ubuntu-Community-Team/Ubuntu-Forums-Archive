---
title: "I cannot network anything!!!"
date: 2006-02-17
forum: Desktop Environments
---

### Post by dylanknightrogers on 2006-02-17
Hi, folks.  I run 2 Ubuntu systems here at home and would like to share data back and forth between the two.

I have installed Samba, smbfs and the NFS packages.

I have the daemons enabled.

All seems well, except whenever I go into Network Servers, it tells me that I have to type in a password.  I type in my user password, but apparently its not good enough.  It asks me again.

I don't know what to do!!! Please help!!

---

### Post by dylanknightrogers on 2006-02-18
never mind.  im not using samba or nfs anymore.

im using ssh.

thanks to all who even decided to choose to help me.

---

### Post by dylanknightrogers on 2006-02-18
Actually, no - the problem's not solved.

I still need to share files and folders with NFS.

For some reason, I can't do it.  Can somebody please guide me step by step?

---

### Post by nalmeth on 2006-02-18
try with no user name or password -- completely blank

or search the forums on howto edit your samba.conf to your needs

I don't think anyone saw your post, and knowing the answer decided not to help you, but I can only speak for myself i guess

---

### Post by Treebeard on 2006-02-18
I haven't setup NFS before..  
but you can also copy files from remote servers with "scp" (secure copy).
You have to run an ssh server, but I assume thats already done.
check "man scp" for options and syntax.

e.g.
```

copy from remote server to local computer:
$ scp user@192.168.0.1:/path/to/files /path/to/destination
<enter password>

copy from local computer to remote:
$ scp /path/to/files user@192.168.0.1:/path/to/destination
<enter password>

``` "user@" is not needed when both use the same user.

---

### Post by dylanknightrogers on 2006-02-18
i keep getting connection refused....

---

### Post by Treebeard on 2006-02-18
Are you able to login with ssh ?

---

### Post by dylanknightrogers on 2006-02-18
no, i am not.  i get a connection refused message from the terminal.

---

### Post by nalmeth on 2006-02-18
any firewall setup?

---

### Post by Treebeard on 2006-02-18
1/ Make sure that ssh is installed on both computers:
```
$ sudo apt-get install ssh
``` This should install the ssh client and server (sshd).

2/ Start ssh daemon on the "remote" computer:
```
$ sudo /etc/init.d/sshd start
``` 
3/ Try to login with ssh on the "remote" computer (e.g. IP address is 192.168.0.1).
```

if the username is the same on both computers:
$ ssh 192.168.0.1

if the username is different on the "remote" computer (e.g. 'user'):
$ ssh user@192.168.0.1

``` 
If you don't know the IP address on the "remote" computer, you can see it with the command 
```
$ sudo ifconfig
``` 
If you can login with ssh, then you are also able to transfer files with secure copy (scp).

4/ If you still get connection refused, see if you have a firewall installed (e.g. firestarter). ssh uses port 22, so make sure that this port is open.

---

