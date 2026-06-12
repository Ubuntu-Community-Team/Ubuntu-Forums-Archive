---
title: "disabling ping"
date: 2006-06-07
forum: Desktop Environments
---

### Post by eeried on 2006-06-07
- Is this the right way of disabling ping?

> This is a kernel parameter that you can set with /etc/sysctl.conf by adding two lines:

# tail -n 2 /etc/sysctl.conf
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_echo_ignore_all = 1


Apply the changes by using the sysctl -p command:

# sysctl -p
.
.
.
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_echo_ignore_all = 1
#

- Can it be done in Firestarter and how? -- When firestarter runs I can't change anything in the settings

- What are the drawbacks of disabling pings?

Many thanks in advance

---

