---
title: "Openswan vpn client to sonicwall"
date: 2008-01-31
forum: Desktop Environments
---

### Post by sridhar_reddapani on 2008-01-31
Hi guys

Did any one successfully configured vpn client using openswan? I am having problems of starting ipsec after making few changes to ipsec.conf the error message i was getting is...

ipsec_setup: (/etc/ipsec.conf, line 31) section header "type=tunnel" has wrong number of fields (1) -- `start' aborted

Any idea?

Thanks.

---

### Post by durb on 2008-03-12
I have had the same problem before, make sure that the file is properly formatted.  All the connection options should be one tab over I believe ( its been a while since I looked at mine).  Like this:

con ...
<tab>options
<tab>options

---

