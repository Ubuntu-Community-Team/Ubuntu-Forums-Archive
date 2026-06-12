---
title: "ssh wont allow me to login??"
date: 2009-06-07
forum: General Help
---

### Post by abhilashm86 on 2009-06-07
when i check ssh with my computer it works fine, i'm newbie to ssh and stuff
```

abhilash@abhilash:~$ ssh abhilash@192.168.1.2
abhilash@192.168.1.2's password: 
Linux abhilash 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sun Jun  7 19:08:31 2009 from abhilash.local
       _                 _                              _     _ 
 _   _| |__  _   _ _ __ | |_ _   _  __      _____  _ __| | __| |
| | | | '_ \| | | | '_ \| __| | | | \ \ /\ / / _ \| '__| |/ _` |
| |_| | |_) | |_| | | | | |_| |_| |  \ V  V / (_) | |  | | (_| |
 \__,_|_.__/ \__,_|_| |_|\__|\__,_|   \_/\_/ \___/|_|  |_|\__,_|
                                                                
Hello abhilash


```

but when i try my friend's system which is also connected with same network, he had some problems in terminal, so he also gave his password, but when i try ssh this error is happening,
```
abhilash@abhilash:~$ ssh someone@192.168.1.2
someone@192.168.1.2's password: 
Permission denied (publickey,password).

```
now why is this error??how to overcome??

---

### Post by upbeat.linux on 2009-06-09
If you are trying to connect to your system from your friend's system on the same network you will need to make sure he is an allowed user. Open /etc/ssh/sshd_config as root and look for a line like:

```
AllowUsers abhilash
```

If the "someone" user is not there you will need to add it after abhilash:

```
AllowUsers abhilash someone
```

then restart ssh:

```
sudo /etc/init.d/ssh restart
```

---

