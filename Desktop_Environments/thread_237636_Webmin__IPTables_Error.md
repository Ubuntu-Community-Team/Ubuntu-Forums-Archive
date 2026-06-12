---
title: "Webmin / IPTables Error"
date: 2006-08-16
forum: Desktop Environments
---

### Post by bpasdar on 2006-08-16
Hello,

I have a brand new installation of Dapper on an IBM T60p.  I have installed webmin since this is how I normally manage my firewall policies.  However when I create a rule set and select the "Apply Configuration" button it gives me the following IPTables error:


Failed to apply configuration :

iptables-restore v1.3.3: Can't use -o with INPUT

Error occurred at line: 7
Try `iptables-restore -h' or 'iptables-restore --help' for more information.


I have also tried to modify the module info and have it apply the policy directly without going to a save file.  It applies it for the session but upon reboot I am back to square one.

This issue seems to apply to my ubuntu installs only two boxes do the same thing, while another distro does not.

Any help is appreciated.

bp

---

