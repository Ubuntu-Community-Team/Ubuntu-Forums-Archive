---
title: "help: dual-boot created dual ssh host keys"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Peatey on 2006-08-25
***[COLOR="Blue"][SIZE="5"]Update: Solution found, see post #4.[/SIZE][/COLOR]***

How can I prevent #3?

Dual-boot is causing a problem due to two different ssh host keys.  How can I merge the two ssh host keys, or otherwise solve the problem?  If I used non-cygwin sshd, would I be able to use the same key?  Flushing the known_hosts file each time seems like a solution tailor-made for thedailywtf.com...

1. Ubuntu Dapper 6.06 running great with sshd:
```
$ ls -al /etc/ssh
drwxr-xr-x   2 Peatey None      0 Aug 25 17:41 .
drwxr-xr-x 110 Peatey None      0 Aug 25 12:34 ..
-rw-r--r--   1 Peatey None 132839 May 17 20:43 moduli
-rw-r--r--   1 Peatey None   1361 May 17 20:43 ssh_config
-rw-r--r--   1 Peatey None   1196 Aug  4 11:07 ssh_host_dsa_key
-rw-r--r--   1 Peatey None   1114 Aug  4 11:07 ssh_host_dsa_key.pub
-rw-r--r--   1 Peatey None   1671 Aug  4 11:07 ssh_host_rsa_key
-rw-r--r--   1 Peatey None    394 Aug  4 11:07 ssh_host_rsa_key.pub
-rw-r--r--   1 Peatey None   1871 Aug  4 11:07 sshd_config

```

2. Windows XP SP2 running Cygwin/X also running sshd:
```
$ ls -al /etc
drwxrwx---+ 10 Peatey Users      0 Aug 25 17:50 .
drwxrwx---+ 11 Peatey Users      0 Jul 25 03:54 ..
...
-rwxr-x---+  1 Peatey Users 132839 Mar 29 07:35 moduli
...
-rwxr-x---   1 Peatey None    1354 Aug 25 17:24 ssh_config
-rw-------   1 SYSTEM None     668 Aug 25 16:35 ssh_host_dsa_key
-rw-r--r--   1 SYSTEM None     604 Aug 25 16:35 ssh_host_dsa_key.pub
-rw-------   1 SYSTEM None     977 Aug 25 16:35 ssh_host_key
-rw-r--r--   1 SYSTEM None     641 Aug 25 16:35 ssh_host_key.pub
-rw-------   1 SYSTEM None    1675 Aug 25 16:35 ssh_host_rsa_key
-rw-r--r--   1 SYSTEM None     396 Aug 25 16:35 ssh_host_rsa_key.pub
-rw-r--r--   1 Peatey None    2845 Aug 25 17:25 sshd_config
...

```
[B]Notice that the ssh_host_???_key* files are owned by SYSTEM and I (Peatey) don't have the permission.
[/B]
3. My other machine (or any other machine for that matter) runs into this problem whenever my laptop switches between Ubuntu and WinXP.
```
$ ssh Peatey@192.168.0.103
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
0a:b1:23:45:67:89:0c:1d:e2:fg:34:56:78:h9:i0:1j.
Please contact your system administrator.
Add correct host key in /home/Peatey/.ssh/known_hosts to get rid of this message.
Offending key in /home/Peatey/.ssh/known_hosts:1
RSA host key for 192.168.0.103 has changed and you have requested strict checking.
Host key verification failed.

```
"Don't dual-boot" isn't the answer: For the time being, I must dual-boot because I need to use MSExcel2003 (I've heard encouraging things about ExcelXP support, but Wine or CrossoverOffice is still not dependable for Excel2003.  OpenOffice.org Calc is still lacking R1C1 reference, pivot-tables, and dependable VBA crossover support).

---

### Post by Woei on 2006-08-25
> **Peatey said:**
> How can I prevent #3?

Dual-boot is causing a problem due to two different ssh host keys.  How can I merge the two ssh host keys, or otherwise solve the problem?  If I used non-cygwin sshd, would I be able to use the same key?  Flushing the known_hosts file each time seems like a solution tailor-made for thedailywtf.com...

1. Ubuntu Dapper 6.06 running great with sshd:
```
$ ls -al /etc/ssh
drwxr-xr-x   2 Peatey None      0 Aug 25 17:41 .
drwxr-xr-x 110 Peatey None      0 Aug 25 12:34 ..
-rw-r--r--   1 Peatey None 132839 May 17 20:43 moduli
-rw-r--r--   1 Peatey None   1361 May 17 20:43 ssh_config
-rw-r--r--   1 Peatey None   1196 Aug  4 11:07 ssh_host_dsa_key
-rw-r--r--   1 Peatey None   1114 Aug  4 11:07 ssh_host_dsa_key.pub
-rw-r--r--   1 Peatey None   1671 Aug  4 11:07 ssh_host_rsa_key
-rw-r--r--   1 Peatey None    394 Aug  4 11:07 ssh_host_rsa_key.pub
-rw-r--r--   1 Peatey None   1871 Aug  4 11:07 sshd_config

```

2. Windows XP SP2 running Cygwin/X also running sshd:
```
$ ls -al /etc
drwxrwx---+ 10 Peatey Users      0 Aug 25 17:50 .
drwxrwx---+ 11 Peatey Users      0 Jul 25 03:54 ..
...
-rwxr-x---+  1 Peatey Users 132839 Mar 29 07:35 moduli
...
-rwxr-x---   1 Peatey None    1354 Aug 25 17:24 ssh_config
-rw-------   1 SYSTEM None     668 Aug 25 16:35 ssh_host_dsa_key
-rw-r--r--   1 SYSTEM None     604 Aug 25 16:35 ssh_host_dsa_key.pub
-rw-------   1 SYSTEM None     977 Aug 25 16:35 ssh_host_key
-rw-r--r--   1 SYSTEM None     641 Aug 25 16:35 ssh_host_key.pub
-rw-------   1 SYSTEM None    1675 Aug 25 16:35 ssh_host_rsa_key
-rw-r--r--   1 SYSTEM None     396 Aug 25 16:35 ssh_host_rsa_key.pub
-rw-r--r--   1 Peatey None    2845 Aug 25 17:25 sshd_config
...

```
[B]Notice that the ssh_host_???_key* files are owned by SYSTEM and I (Peatey) don't have the permission.
[/B]
3. My other machine (or any other machine for that matter) runs into this problem whenever my laptop switches between Ubuntu and WinXP.
```
$ ssh Peatey@192.168.0.103
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
0a:b1:23:45:67:89:0c:1d:e2:fg:34:56:78:h9:i0:1j.
Please contact your system administrator.
Add correct host key in /home/Peatey/.ssh/known_hosts to get rid of this message.
Offending key in /home/Peatey/.ssh/known_hosts:1
RSA host key for 192.168.0.103 has changed and you have requested strict checking.
Host key verification failed.

```


I may be stating the obvious here, but have you tried copying the keys and the modulus file from one install to the other ? It doesn't matter which one going to which.

The error message you're seeing is just ssh's way of saying there might be a man in the middle attack. Basically, authentication in SSH is two-way. You identify yourself to the server through whatever means is configured (password authentication, rhost, private keys) but the other way around happens too: the server sends its public key to you during the handshaking process during which a symmetric cypher is negotiated through the much slower public/private key system. SSH stores the public key of servers it has connected to in your ~/.ssh/known_hosts file to protect you against attackers that want to eavesdrop on your communication by pretending to be the server, while in fact setting up a dual communication between you and the attacker, and the attacker and the real target server.

---

### Post by Peatey on 2006-08-25
Thanks Woei, but i can't copy the keys in either direction because I can't read from or write to the cygwin version (owned by user SYSTEM).  I'd try copying if I could.

---

### Post by Peatey on 2006-08-25
Solved:  A friend reminded me of ```
chown
``` and now no more fingerprint warnings.  :D 

Here are the steps:

1. stop sshd ($ net stop sshd)
2. change ownership of cygwin's ssh host keys to mine.
3. copy/replace ubuntu's ssh host keys (in /etc/ssh) into cygwin (in /etc). might want to make a backup first.
4. change ownership of the new keys back to SYSTEM.
5. restart sshd ($ net start sshd)

Now no matter what OS I boot my laptop with, ssh server is running as service and nothing has changed from any client's perspective.  

yes, it was trivial issue in hindsight, but par for the course for a linux newbie like me.

---

