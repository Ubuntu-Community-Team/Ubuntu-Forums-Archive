---
title: "Need help starting vpn service on boot-up"
date: 2006-02-15
forum: Desktop Environments
---

### Post by UphillSkier on 2006-02-15
Greeting, ubuntu friends

I use a cisco vpn client to connect to my university.  To work, it needs to load a kernel module.  I can do it manually with
```
sudo -i
root@grumpy:~# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
```

but I want it to load automatically at boot-time.  So I make a symbolic link in rc5.d

```
root@grumpy:/etc/rc5.d# ln -s ../init.d/vpnclient_init  S85vpnclient_init
ls -lF S*
lrwxrwxrwx  1 root root 24 Feb 15 21:14 S85vpnclient_init -> ../init.d/vpnclient_init*

```

and reboot but the module is not loaded.  When I try to connect I get 
 
```
andy@grumpy:~/Desktop$ vpnclient connect McMasterVPN
Cisco Systems VPN Client Version 4.7.00 (0640)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.

```

If I load the module manually, all is well.  So what is going on?  I thought that this was the way to start services on boot-up.  Can someone point out what I am doing wrong?

thanks very much

---

### Post by dcstar on 2006-02-16
[QUOTE=UphillSkier]Greeting, ubuntu friends

I use a cisco vpn client to connect to my university.  To work, it needs to load a kernel module.  I can do it manually with
```
sudo -i
root@grumpy:~# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
```

but I want it to load automatically at boot-time.  So I make a symbolic link in rc5.d

```
root@grumpy:/etc/**rc5.d**# ln -s ../init.d/vpnclient_init  S85vpnclient_init
ls -lF S*
lrwxrwxrwx  1 root root 24 Feb 15 21:14 S85vpnclient_init -> ../init.d/vpnclient_init*

```
.........[/QUOTE]
Most of us load up in run level 2, why are you using 5?

---

### Post by UphillSkier on 2006-02-16
[QUOTE=dcstar]Most of us load up in run level 2, why are you using 5?[/QUOTE]

Good question.  Somehow I thought that run-level 5 was for X and since I was using X it was reasonable to startup with rc.d.  But I just checked, and the link is in rc3.d, rc4.d and rc5.d, but not rc2.d.  I will try fixing that.

BTW, does this mean that Ubuntu is generally in run level 2 for user operations?

Thanks for your help
Andy

---

