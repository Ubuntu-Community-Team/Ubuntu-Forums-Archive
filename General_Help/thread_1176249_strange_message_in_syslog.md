---
title: "strange message in syslog"
date: 2009-06-02
forum: General Help
---

### Post by Peter09 on 2009-06-02
I have the following message occurring in Syslog, can anyone provide an idea as to what is happening.

> nss_wins[3833]: synchronized to 130.88.200.4, stratum 2

Whois shows 130.88.200.4 to be Manchester University.... with whom I have no connection.

I have seen someone else with the same problem on the Internet, but they did not get an answer....

Can anyone suggest anything?

---

### Post by Peter09 on 2009-06-02
I presume this is a time service but I always thought that was ntp - and what is the wins part?

---

### Post by iponeverything on 2009-06-02
It looks like your running samba.

---

### Post by Peter09 on 2009-06-02
Yes I am running Samba, but why should Samba be doing this?

---

### Post by Peter09 on 2009-06-03
Bump

---

### Post by capscrew on 2009-06-03
> **Peter09 said:**
> Yes I am running Samba, but why should Samba be doing this?

Interesting.  That IP address is shown as the NTP stratum 2 time server for Manchester University.  See _[here]("http://http://www.timetools.co.uk/ntp-servers/ref/ntp-servers-uk.htm")_

In the past there have been problems with syslog_ng logging everything as nss_wins.  Are you using syslog_ng?  Are you using NTP?

---

### Post by Peter09 on 2009-06-04
Just the standard Jaunty distribution.

---

### Post by Yellow Pasque on 2009-06-04
NTP = time server, keeping your system clock synchronized
System -> Administration -> Time and Date

---

