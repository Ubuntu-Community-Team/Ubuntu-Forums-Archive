---
title: "Blocked SSL, imap, and putty"
date: 2008-09-15
forum: Desktop Environments
---

### Post by Roosta21 on 2008-09-15
Im a newbie,

I updated this morning using adept..

Now Thunderbird will not connect to the Imap server any https website times out and cant connect to my servers using putty.

I have tried to stop the iptabes running using the below link as a guide (ubutu guide)

but to no avail

[http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/](http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/)

---

### Post by Roosta21 on 2008-09-16
Bump 

Really stuck guys any help would be appreciated!

---

### Post by DPJB on 2008-09-16
Hi,

What is the output of iptables -L? (in a terminal)

If there is any, you can flush all firewall rules by running this from a terminal: sudo iptables -F

This will just work for the current session...

If this doesn't work, it is not your firewall.

Cheers!

Dirk

---

