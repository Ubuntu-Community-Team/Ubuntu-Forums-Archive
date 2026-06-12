---
title: "FreeNX Installation"
date: 2009-01-19
forum: General Help
---

### Post by islandergeek on 2009-01-19
Hi all, I've been banging my head on this all day (searched these forums numerous times) and I'm now falling asleep and ready to give up...

I'm trying to install FreeNX server so I can access it from my MacBook, should be simple right? I thought it would but I can't get passed that authorization failed issue:
[LIST=1]
[*] SSHing as NX user from my Mac into Ubuntu works so SSH keys are OK
[*] Doing nxserver --useradd and nxserver --usercheck on the Ubuntu box both work and report success
[/LIST]
However trying to use the NoMachine Mac client to login reports authentication failure with grayed out 'details' button. It passes the SSH login but then fails to login the user. It is not the 'known_hosts' issue reported in this forum, I have wiped out this file numerous times. 

Using the NX protocol directly doesn't yield much more info:
```

~ $ >ssh nx@rmk -p 2005 
HELLO NXSERVER - Version 3.3.0-14 - LFE
NX> 105 HELLO NXCLIENT - Version 1.5.0
Hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
Set shell_mode: shell
NX> 105 SET AUTH_MODE PASSWORD
Set auth_mode: password
NX> 105 login
Login 
NX> 101 User: islandergeek
islandergeek
NX> 102 Password: ************
NX> 404 ERROR: wrong password or login.
NX> 999 Bye.

```

I'm out of ideas at this point, if any brave soul has some ideas to share I would be forever grateful...

Thanks.

---

### Post by gettinoriginal on 2009-01-19
Hate to sound dumb here, but are you sure that your password is properly cased ?? (caplock on or off)  or that you did not use "odd" characters, only letters/numbers.

---

### Post by islandergeek on 2009-01-19
Yeah it sounds as if the passwords don't match but I checked a gazillion times that they did. I can SSH using my user just fine:
```

ssh islandergeek@rmk -p 2005
Linux Rmk 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

  System information as of Mon Jan 19 10:00:01 PST 2009

  System load: 1.68               Memory usage: 71%   Processes:       179
  Usage of /:  40.3% of 67.11GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
Last login: Mon Jan 19 09:51:55 2009 from [...]
islandergeek@Rmk:~$ 

```

Well actually that doesn't mean much since I'm using key authentication. :P But yeah I also checked my password.
Thanks for replying though.

---

### Post by gettinoriginal on 2009-01-19
Found this about editing the file about username and password DB in FreeNX, maybe checking this site will help ??  Sorry, just trying to help. :confused:

---

### Post by islandergeek on 2009-01-19
Thanks for the help, it seems the link is missing though? In any case I'm not sure it will help as I am not using the password DB but key authentication instead. Bah this is hopeless :P

---

### Post by gettinoriginal on 2009-01-19
Well, I have been reviewing many other threads, and I cannot find one using 
key authentication that lists error 404 with username/password, so I guess I am no further help, sorry.  But I wish you good luck.  :)

---

### Post by islandergeek on 2009-01-19
Not marking this solved as I still can't make it work using just keys but I ended up enabling NX's password database and authorization now works.

---

### Post by FrankT-Qc on 2010-04-18
HI there !!!

FreeNX authenticates the user by many means... In the basic setup, it does so by ssh. If your ssh does not accept passwords, you're screwed. 

Edit /etc/nxserver/node.conf and make sure you have :
```

ENABLE_SSH_AUTHENTICATION="0"                                                                                                                                
ENABLE_SU_AUTHENTICATION="1"     

```

ciao

---

