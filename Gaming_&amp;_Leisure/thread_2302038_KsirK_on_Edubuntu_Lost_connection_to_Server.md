---
title: "KsirK on Edubuntu Lost connection to Server"
date: 2015-11-07
forum: Gaming &amp; Leisure
---

### Post by peter169 on 2015-11-07
I'm trying to run KsirK on endubuntu.
When I try to "Join Standard TCP/IP network game" using Host: localhost Port: 20000 (these are default, I don't know what else to use), I get the message "Lost connection to server". This comes up straight away.

---

### Post by efflandt on 2015-11-07
Are you running the server (New Standard TCP/IP Network Game) on the same computer? The **localhost** name is always loopback to your own computer (127.0.0.1). If you are trying to connect to that from another computer on your LAN, you need to use the LAN IP of the server and make sure that port 20000 is not firewalled by something on the server. To find the LAN IP of the server use the **ipconfig** command in a terminal on the server (or from ssh connection to the server).

---

### Post by peter169 on 2015-11-07
k

---

