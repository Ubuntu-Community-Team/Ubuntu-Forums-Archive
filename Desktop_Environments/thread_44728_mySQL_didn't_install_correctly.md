---
title: "mySQL didn't install correctly"
date: 2005-06-27
forum: Desktop Environments
---

### Post by cope on 2005-06-27
hey,

**************** SHORT INTRODUCTION *******************

i'm new to ubuntu and like what i see so far..
i'm fairly new to the *nix scene, while dabbling a little bit with some previous versions of redhat. at the moment the reason i grabbed a copy, to tell you the truth, was because i needed a cheap server that would run a tomcat apache type setup, so i can build some web apps.... But all in all, out of all the distro's out there, i think ubuntu will be the easiest to understand and grow with!
good works guys! \\:D/ 

so, theres thje intro :)
now the problem!

**************** PROBLEM DESCRIPTION STARTS HERE *******************

so i stumbled across the "Unofficial Ubuntu 5.04 Starter Guide"!
i tried to download install mySQL, php & mySQL to start off with!
apache & php worked fine! when i tried to download mySQL it threw an error but still kindof workeed..... i found that i needed to add Repositories??? :)
so i did, by following [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

i then attempted to add mySQL again
sudo apt-get install mysql-server
but it says
```

mark@amd1000:~$ sudo apt-get install mysql-server
Password:
Reading package lists... Done
Building dependency tree... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
mark@amd1000:~$

```

but when i try to run MySQLCC it doesn't run and comes up with the error.,
```

Cannot launch entry

Details: Failed to execute child process "mysqlcc" (No such file or directory)

```

how do i uninstall mySQL and try to run the install again?
or is there something i'm not doing right?

if anyone is still reading, thanks ;)  ](*,)

---

### Post by intangible on 2005-06-27
/*** Solution Starts Here :D ***/

You can remove mysql using the dpkg command:
**sudo dpkg --purge mysql-server**
and then add it again:
**sudo apt-get install mysql-server**

OR you could just try reinstalling it:
**sudo apt-get --reinstall install mysql-server**

/*** End Solution ***/

Have you tried out Synaptic yet?  It will help you manage program packages and you can remove and add them quite easily. It's at: **System->Administration->Synaptic Package Manager**

Let me know if you have anymore trouble, have fun!

---

### Post by cope on 2005-06-27
thanks for the prompt reply!

i've installed it fine.. it configures packages and install finishes correctly!

but i'm unable to choose a root password for the mySQL server. 
everytime i try below happens.

```

mark@amd1000:~$ mysqladmin mysqladmin -u root password apassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

```

any thoughts? if i mysqld it complains the server is running
```

mark@amd1000:~$ mysqld
050628  2:59:33 Warning: Can't create test file /var/lib/mysql/amd1000.lower-test
Warning: One can only use the --user switch if running as root
050628  2:59:33 Can't start server : Bind on unix socket: Address already in use
050628  2:59:33 Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
050628  2:59:33 Aborting

050628  2:59:33 mysqld: Shutdown Complete

```

if i ps a. it doesn't show the server running..
tutorials tend to fly through this bit, as they think it'll just work!  ](*,)

---

### Post by cope on 2005-06-27
i think i got it ;)
mysql -u root -p

then hit enter, then i can enter the password rather then
mysql -u root -p password

---

### Post by intangible on 2005-06-28
Sorry about the delay in replying, your post didnt show up in my recent activites ?  Glad you got it

---

