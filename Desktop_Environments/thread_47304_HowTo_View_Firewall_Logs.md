---
title: "HowTo View Firewall Logs?"
date: 2005-07-08
forum: Desktop Environments
---

### Post by Kadaver on 2005-07-08
Hi there all you intelligent people,

So how do i view the firewall logs generated?

Can i view these to indicate the amount of data moved over a specific interface, and on what port how much was moved.

Oh yes, and a nice graphical or numeric presentation would also be lovely  ;-) 

Thx

---

### Post by dataw0lf on 2005-07-08
Yes to all questions.  As far where they log to, check what your iptables have setup (you specify how and where to log in iptables rules).  /var/log/messages is a good place to check, for default rules.

---

