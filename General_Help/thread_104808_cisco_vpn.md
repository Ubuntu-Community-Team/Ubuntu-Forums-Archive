---
title: "cisco vpn"
date: 2005-12-16
forum: General Help
---

### Post by Zaventh on 2005-12-16
Anyone know of a way to setup a cisco vpn client with group authentication? I've looked into "vpnc" a bit, but it doesn't appear to support group authentication.

---

### Post by hajk on 2005-12-17
The Ubuntu package "vpnc" does allow group authentication... Below is the 
configuration file for VPN access to my university (with some information 
masked to protect the innocent): 

IPSec gateway <IPnumber>
IPSec ID <groupID> 
IPSec secret <groupSecret>
XAuth username <userName>

Lines 2 and 3 are about group authentication; if you leave these out, then
groupID and groupSecret will be asked for interactively (as is already the case 
with userPassword).

---

### Post by maglis on 2005-12-17
I confirm that vpnc works fine. 

You may try:

vpnc --help 
or
vpnc --long-help

and check if cisco router you are trying to connect to is supporting only 1-des encryption with 'vpnc --enable-1des' option...

---

