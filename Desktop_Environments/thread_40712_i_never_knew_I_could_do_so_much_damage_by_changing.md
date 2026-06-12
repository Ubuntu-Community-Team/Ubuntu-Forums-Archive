---
title: "i never knew I could do so much damage by changing my firewall settings"
date: 2005-06-10
forum: Desktop Environments
---

### Post by Nada_Surf on 2005-06-10
At least I think its my firewall settings.

I installed Warty and have been experimenting with samba, postfix etc.

I installed Webmin and its been helping a lot.  I found the Linux Firewall module and enabled it and then proceeded to remove all access from all ports.  So now I can pretty much do nothing with the machine.

Cant access the webserver, ftp, ssh, samba shares or even WEBMIN to reset the firewall.

The last kick in the nuts is that the box takes about 30 mins to boot after login now....

any ideas?  How do I reset the firewall/turn it off manually?

-- I think I need to reset my iptables, how is this done?

---

### Post by djg on 2005-06-10
"iptables -F" is worth a try.

---

