---
title: "gdm problems linked to network configuration bug"
date: 2006-07-25
forum: Desktop Environments
---

### Post by milou on 2006-07-25
Hello.
I got into problems, with breeezy and now with dapper drake.

I think I found a bug, at least on my computer (D900t laptop).
When changing the network configuration without deactivating the interface, it bombs, reset, and all the configuration files linked to network configuration are crashed (/etc/hosts, /etc/host.conf,/etc/network/intefaces etc...) !!!!
The first time it happened with me was with breezy, and that was a mess, so I decided to install dapper.
But the same thing happened yesterday, in the same configuration, changing network config without deactivating the network ! ](*,) .
I succeeded this time to recover the crashed files, but now I have a problem with gdm I did not have before.
I use PostLogin to connect a samba server to user home when the user is connecting. I have a "mount -t smbfs ..." line in /etc/gdm/PostLogin/Default.
When I connect with gdm with any user, I have the following message in /var/log/syslog :

set config key daemon/PostLoginScriptDir to string /etc/gdm/PostLogin
gdm_slave_exec_script: Failed starting: /etc/gdm/PostLogin/Default

But what is surprising is that the PostSession file is working ok (I tested it by creating a TTT directory, and adding a line "rmdir /home/$USER/TTT" in PostSession file).

Can someone help me with this problem ??? I really don't know where the problem can be :(  ...

Eric

---

