---
title: "failed again"
date: 2009-03-07
forum: General Help
---

### Post by grubster on 2009-03-07
I tried another port scan test but it failed again due to my reply to a ping. I used this code in a terminal but it hasnt worked any suggestions?

sudo su -c "echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all"

---

### Post by brian_p on 2009-03-07
> **grubster said:**
> I tried another port scan test but it failed again due to my reply to a ping. I used this code in a terminal but it hasnt worked any suggestions?

sudo su -c "echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all"

Works here. Check file contents with

```
cat /proc/sys/net/ipv4/icmp_echo_ignore_all
```

Is the machine connected to a router?

---

