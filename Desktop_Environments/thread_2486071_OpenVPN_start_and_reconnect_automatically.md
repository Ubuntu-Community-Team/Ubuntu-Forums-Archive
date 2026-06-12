---
title: "OpenVPN start and reconnect automatically"
date: 2023-04-19
forum: Desktop Environments
---

### Post by nixnoob2 on 2023-04-19
Hi,
I would love to have OpenVPN start and try to connect after machine boots, and try to re-connect if disconnected.

Have tried (restarting machine after each change).

- Un-comment "AUTOSTART="all"" in */etc/default/openvpn* file 
- Add "--ping-restart 10" into */etc/openvpn/client/myvpn.conf* file

If I do 'systemctl status openvpn' it is 'active (exited)'.

There are no log files in */var/log/openvpn*, and I can't find anything useful in other logs, maybe I can increase log level somewhere?

I noticed that there is no openvpn in */etc/systemd/system*, is this right as I thought service needs to be in here so it can know pre-requisite required (the 'wants' file)? I am new to Linux just trying to figure out how this works.
Thanks in advance, I have spent hours trying various things with hard luck.

ps. If I try to connect manually it works everytime.

Cheers,
Jay

---

### Post by ActionParsnip on 2023-04-19
Making a systemd module to run the commands you need

---

### Post by nixnoob2 on 2023-04-19
Thanks, that is not obvious as most information I found just mentions to uncomment the AUTOSTART=all.

When I check services now with ]systemctl list-unit-files --type=service'

openvpn.service                            enabled         enabled      
openvpn@.service                           disabled        enabled      

But still not getting openvpn to autoconnect? Could something be corrupted, I will try remove openvpn and start from scratch but hoping someone can point me closer to a solution or an alternative to openvpn

---

### Post by ActionParsnip on 2023-04-20
Something like this
[https://www.ivpn.net/knowledgebase/linux/linux-autostart-openvpn-in-systemd-ubuntu/](https://www.ivpn.net/knowledgebase/linux/linux-autostart-openvpn-in-systemd-ubuntu/)

---

### Post by nixnoob2 on 2023-04-23
Thanks, after reinstalling it is working on startup.

---

### Post by ActionParsnip on 2023-04-24
Great. Please mark as solved if there is no more issue here

---

