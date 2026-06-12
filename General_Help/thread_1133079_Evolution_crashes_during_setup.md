---
title: "Evolution crashes during setup"
date: 2009-04-22
forum: General Help
---

### Post by jims2321 on 2009-04-22
I recently installed Ubuntu 9.04 on my pc.  When I try to configure Evolution Mail to connect to my company Exchange server, it crashes during authenticate process on the Receiving Email setup page.  

I have version 8.10 on a thumb drive, and the same setup choices, work just fine.

Any idea where to begin to debug this issue.  FYI, if I use Firefox to connect to the exchange server (OWA), it works fine.

---

### Post by cmnorton on 2009-04-22
First, start looking in the logs (/var/log) to see if any tell-tale messages were left there.

Here's a debugging link:

[http://projects.gnome.org/evolution/bugs.shtml](http://projects.gnome.org/evolution/bugs.shtml)

---

### Post by jims2321 on 2009-04-22
get the following output from debug

e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'

---

### Post by r-mo on 2009-04-24
I get the same thing, just about to raise a bug report.  I've managed to get round it though by using the new MAPI extensions to evolution.

sudo apt-get install evolution-mapi

Then choose server type 'Exchange MAPI' instead of 'Microsoft Exchange' when you setup the account.

---

### Post by r-mo on 2009-04-24
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/365939](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/365939)

---

