---
title: "ssh &amp; kubuntu problem"
date: 2009-12-21
forum: Desktop Environments
---

### Post by Sergey Novikov on 2009-12-21
Hi, sorry for probably bad english.

I installed kubuntu 9.10, then openssh-server and now I have a problem with ssh connection to my machine. So when I log in through kdm to KDE session - I can connect to kubuntu, but when I log out from user's KDE session connection fails.

I have real internet ip on eth0

From console (ctrl+alt+F1) I see that sshd is running
iptables -L:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

When I try connect is see attempts through "tcpdump -i eth0 port 22"
but no answers from sshd returns.

Thanks for any help.

---

### Post by Zorael on 2009-12-21
If you connect from within KDE, it uses NetworkManager (via the knetworkmanager frontend), and technically the connection is made in a session for a session. Logging out, it will promptly disconnect.

I think you'll have to disable NetworkManager completely and connect either manually via ifconfig/iwconfig, or specify the connection in **/etc/network/interfaces**.

I'm not sure how **wicd** behaves, though. Perhaps it allows the connection to persist even after having logged out.

---

### Post by Sergey Novikov on 2009-12-22
> **Zorael said:**
> If you connect from within KDE, it uses NetworkManager (via the knetworkmanager frontend), and technically the connection is made in a session for a session. Logging out, it will promptly disconnect.

I think you'll have to disable NetworkManager completely and connect either manually via ifconfig/iwconfig, or specify the connection in **/etc/network/interfaces**.

I'm not sure how **wicd** behaves, though. Perhaps it allows the connection to persist even after having logged out.

Thank you. Indeed, you are right. NetworkManager shut down ethernet port when I log out from KDE session.

---

