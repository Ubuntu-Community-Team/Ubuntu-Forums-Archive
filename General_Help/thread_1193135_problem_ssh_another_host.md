---
title: "problem ssh another host"
date: 2009-06-21
forum: General Help
---

### Post by mmbathan on 2009-06-21
[B]Hi all,

I try to connect to another host using ssh but I got this problem in virfication while I enter the correct password.[/B]

bagside@bagvapp:~$ sudo ssh -D 1080 192.168.137.111
[sudo] password for bagside:
The authenticity of host '192.168.137.111 (192.168.137.111)' can't be established.
RSA key fingerprint is cb:ba:eb:b4:be:52:95:dd:7a:00:52:ba:37:f4:94:59.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.137.111' (RSA) to the list of known hosts.
root@192.168.137.111's password: 
Permission denied, please try again.
root@192.168.137.111's password: 
Permission denied, please try again.
root@192.168.137.111's password: 
Permission denied (publickey,password).

**Also, I modify the the option of login from the root in the file  **/etc/ssh/sshd_config 
# Authentication:
LoginGraceTime 120
PermitRootLogin [COLOR="Red"]yes[/COLOR]
StrictModes yes

**and I restart the ssh **
#/etc/init.d/sshd restrat

[B]and the problem is still.

could any one help me please

Regards,[/B]

---

### Post by Thyme on 2009-06-21
Maybe:

sudo ssh -D 1080 root@192.168.137.111

---

### Post by mmbathan on 2009-06-21
**thank you Thyme for your respond**

**I tried your command and still the same problem.**

bagside@bagvapp:~$ sudo ssh -D 1080 192.168.137.111
[sudo] password for bagside:
root@192.168.137.111's password: 
Permission denied, please try again.
root@192.168.137.111's password: 
Permission denied, please try again.
root@192.168.137.111's password: 
Permission denied (publickey,password).


[B]any other suggestions.

Regards,[/B]

---

### Post by paperplate9 on 2009-06-21
Assuming "#/etc/init.d/sshd restrat" is a typo (restrat->restart), you must have the wrong password for **root**.

Be aware that by default root does not have a password on Ubuntu unless you specifically set one...I won't get into that.

Also, I don't think there's any reason to "sudo" an ssh command....

My guess is that you're using your "bagside" password thinking that sudo'ing with it will get you into root's account (via ssh).

---

### Post by blueridgedog on 2009-06-21
+1  Test with a normal account first.

---

### Post by mmbathan on 2009-06-21
**thank you guys **
 
**I tried **
 
[EMAIL="bagside@bagvapp:~$"]bagside@bagvapp:~$[/EMAIL] ssh -D 1080 192.168.137.111
The authenticity of host '192.168.137.111 (192.168.137.111)' can't be established.
RSA key fingerprint is cb:ba:eb:b4:be:52:95:dd:7a:00:52:ba:37:f4:94:59.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.137.111' (RSA) to the list of known hosts.
[EMAIL="bagside@192.168.137.111's"]bagside@192.168.137.111's[/EMAIL] password: 
Permission denied, please try again.
[EMAIL="bagside@192.168.137.111's"]bagside@192.168.137.111's[/EMAIL] password: 
Permission denied, please try again.
[EMAIL="bagside@192.168.137.111's"]bagside@192.168.137.111's[/EMAIL] password: 
Permission denied (publickey,password).

 
**and I used the bagside password and the other host password and it the same problem**

---

### Post by blueridgedog on 2009-06-21
On the server in question, ssh to 127.0.0.1 and verify that it works in a purely local fashion.

---

### Post by paperplate9 on 2009-06-21
1. What is the name of the account on 192.168.137.111 that you're trying to get into?
2. Do you know the password for **that** account on 192.168.137.111?

---

### Post by mmbathan on 2009-06-21
[EMAIL="user@ubuntu8041:~$"][COLOR=#0068cf]user@ubuntu8041:~$[/COLOR][/EMAIL] ssh 127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is cb:ba:eb:b4:be:52:95:dd:7a:00:52:ba:37:f4:94:59.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
[EMAIL="user@127.0.0.1's"][COLOR=#0068cf]user@127.0.0.1's[/COLOR][/EMAIL] password: 
Linux ubuntu8041 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
To access official Ubuntu documentation, please visit:
[[COLOR=#0068cf]http://help.ubuntu.com/[/COLOR]]("http://help.ubuntu.com/")
[EMAIL="user@ubuntu8041:~$"][COLOR=#0068cf]user@ubuntu8041:~$[/COLOR][/EMAIL] 

 
**1. What is the name of the account on 192.168.137.111 that you're trying to get into?**
user

[B]2. Do you know the password for that account on 192.168.137.111? 
[/B]user

---

### Post by blueridgedog on 2009-06-21
Are you certain that sshd is listening on all IP addresses?  Have you adjusted /etc/ssh/sshd_config?

---

### Post by mmbathan on 2009-06-21
**I just  modified the the option of login from the root in the file **/etc/ssh/sshd_config 

# Authentication:
LoginGraceTime 120
PermitRootLogin [COLOR=red]yes[/COLOR]
StrictModes yes

---

### Post by paperplate9 on 2009-06-21
> **mmbathan said:**
> **1. What is the name of the account on 192.168.137.111 that you're trying to get into?**
user

[B]2. Do you know the password for that account on 192.168.137.111? 
[/B]user


```
bagside@bagvapp:~$ ssh -D 1080 user@192.168.137.111
```Use the password you supplied...


...and you can change PermitRootLogin back to no since you're not even trying to log into the 'root' account!

---

### Post by mmbathan on 2009-06-21
**yaaaaaah it is working now**
 
**thank you guys**

---

