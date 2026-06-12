---
title: "firestarter configuration problem"
date: 2006-06-13
forum: Desktop Environments
---

### Post by m487396 on 2006-06-13
Hello,

I'm trying to configure firestarter on Ubuntu Dapper.

I have a DSL modem connected to eth1 and an ethernet connection to my
laptop on eth0.

Using the wizard, I've chosen:
detected devices: eth1
start the firewall on dial-out: unchecked
IP address via DHCP: checked
enable internet sharing: unchecked
start firewall now: checked

When I start the firewall and visit a site with Firefox, Firefox gives
me the message Connecting to <site>... and then stops.

I see no events in the events panal, and I haven't set any other
policy.

How can I go about diagnosing my problem? Suggestions gratefully
recieved. I've attached the output from 'sudo iptables --list' if
that's helpful. Thanks,

- mark

---

### Post by Subnet on 2006-06-13
[QUOTE=m487396]
enable internet sharing: unchecked
[/QUOTE]

Have you tried enabling internet sharing?

---

### Post by m487396 on 2006-06-13
Yes. Same result, I'm afraid. Thanks for the suggestion.

---

### Post by Subnet on 2006-06-13
What about the dhcp package?

---

### Post by m487396 on 2006-06-14
[QUOTE=Subnet]What about the dhcp package?[/QUOTE]
Yes, I have  dhcp3-client, dhcp3-common. Thanks,

- mark

---

