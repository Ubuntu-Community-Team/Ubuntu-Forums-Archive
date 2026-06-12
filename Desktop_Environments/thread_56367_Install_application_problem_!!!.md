---
title: "Install application problem !!!"
date: 2005-08-12
forum: Desktop Environments
---

### Post by dotdotdot on 2005-08-12
I have just installed Kubuntu 5.04 and tried to install the Ciscos VPN client software.But it asked me to input where it can get the kernel source code.like this:

[[IMG]http://img352.imageshack.us/img352/9472/ciscoinstall5ph.jpg[/IMG]](http://imageshack.us)

but in Kubuntu i didn't see anything says kernel source.

Then i downloaded the kernel source code from internet and unpacked.then gave the link to the install program.It did run but said alot of errors and finally it said cannot make module cisco blah blah blah...

Like this:
[[IMG]http://img361.imageshack.us/img361/6048/ciscoinstall13gu.jpg[/IMG]](http://imageshack.us)

Please help.
Thanks in advanced

---

### Post by dotdotdot on 2005-08-12
Now i can fix this problem as :

Install package "linux-headers-2.10.5-386"

Then it automatically has the kernel source headers to install the program.

But I have an other problem while running the program,it said :

[i]"root@louisUbuntu:/usr/src/vpnclient # vpnclient connect Swinburne_External
Cisco Systems VPN Client Version 4.6.02 (0030)
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system."[/i]

So what is "Is kernel module loaded?" ?

I have no idea.

---

### Post by GeneralZod on 2005-08-12
[QUOTE=dotdotdot]

So what is "Is kernel module loaded?" ?

I have no idea.[/QUOTE]

This is a 100% guess but try:

```
sudo modprobe cisco_ipsec 
```

Be warned, though - if I'm wrong, this may crash your machine!

---

### Post by mholst on 2005-12-02
Hi There.

U have to start the cisco client by writing the following:

sudo /etc/init.d/vpnclient_init start

And then connect by:
vpnclient connect <vpn_profile>

---

