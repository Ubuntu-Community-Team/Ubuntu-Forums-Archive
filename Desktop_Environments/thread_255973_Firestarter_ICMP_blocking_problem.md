---
title: "Firestarter ICMP blocking problem"
date: 2006-09-12
forum: Desktop Environments
---

### Post by alekz on 2006-09-12
Hi, i have a problem with firestarter, it is blocking me traceroute replies so i can't perform any traceroute, i've checked firestarter's preferences and i have checked the "Allow traceroute" option, so i can't find where the problem is, when i shut down the firewall traceroute works with no problem.

Thanks for ur replies.

---

### Post by lupine_nickt on 2006-09-12
By default, linux traceroute uses UDP packets.

Try installing tcptraceroute, or using traceroute -I (to use ICMP)

xF,

...Nick

---

### Post by alekz on 2006-09-12
Hi Nick thanks for ur replie but still not working... it just fall in a loop :S any idea ?

---

### Post by jamesford on 2006-09-12
i have this problem too, the only fix i know of is to install firesterter, set up your rules (like opening torrent ports) reboot and uninstall firestarter again. rules will stick but the traceroute problem is gone and so is other problems like firestarters incompability with for example moblock

---

