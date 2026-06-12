---
title: "Remote ssh hangs when connecting"
date: 2022-09-10
forum: Debian
---

### Post by fignupafya on 2022-09-10
I installed Debian to my old laptop to use it as a server locally and remotely. I can shh to it on the same network but i can't connect to it from another network. When i ssh to it remotely it hangs and it does not return any error. I port forwarded port 22 to port 22 of 192.168.1.103 and modified the GatewayPorts as yes on /etc/ssh/sshd_config file. I am new into these and i don't know what am i doing wrong, maybe wrong ssh command, port forwarding or something else. I would be happy for your help. :)

Note:
With -vvv parameter it does not return "debug1: Connection established." and it hangs there when connecting to it remotely.

---

### Post by TheFu on 2022-09-10
Check the router, firewall in the router and firewall on the system.

Troubleshooting ssh: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has steps to determine the issue.

---

