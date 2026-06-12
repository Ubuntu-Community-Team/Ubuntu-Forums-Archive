---
title: "How do I disable UDP firewall?"
date: 2009-04-07
forum: General Help
---

### Post by kevincolorado on 2009-04-07
How do I disable UDP firewall?

Thank You

---

### Post by mb_webguy on 2009-04-08
It shouldn't be enabled by default.  In a terminal, run the command "sudo iptables -L".  You should see something like:```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If it doesn't say this, you can use the following commands to set things right.```
sudo ufw default accept
sudo ufw enable
```

---

