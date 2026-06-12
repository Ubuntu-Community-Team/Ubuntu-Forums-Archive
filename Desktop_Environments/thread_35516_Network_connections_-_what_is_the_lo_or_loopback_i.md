---
title: "Network connections - what is the lo or loopback interface ?"
date: 2005-05-19
forum: Desktop Environments
---

### Post by davegahan on 2005-05-19
I have sometimes a problem connecting to the web - cant get the ethernet card in my laptop to work...  my system by default enters in "lo" or "loopback interface" as standard network connection.  What is that lo connection and what purpose does it serve ?

When I switch locations I sometimes need to reconfigure my ethernet connection, even with dynamic IP adresses. When I have such issue my default network connection is "loopback interface"

---

### Post by sfw5000 on 2005-05-19
Without getting into the specifics of why, suffice to say you have to have the loopback interface enabled for the system to work... it will always be there. If you only see the lo connection instead of, say, the eth0 connection, then it means your ethernet card is not configured properly... If you issue the command ```
ifconfig -a
``` you should be able to see more details about your ethernet card and why it isn't working.

If you are switching locations a lot, it could be that some of the networks you join don't use DHCP or something like that... generally, though, it sounds like it does work?

---

