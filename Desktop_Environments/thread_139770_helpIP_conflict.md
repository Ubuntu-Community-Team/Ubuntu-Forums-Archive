---
title: "help:IP conflict"
date: 2006-03-04
forum: Desktop Environments
---

### Post by vincent339 on 2006-03-04
When someone got the same IP in LAN,I couldn't use http,ftp and so on.And ubuntu didn't tell me any thing about it.Every time I have to use "/etc/init.d/networking resart" again and again.How can I know it just when someone uses the same IP.

---

### Post by andrewsawyer on 2006-03-04
I take it you don't have DHCP set up on the router?

---

### Post by vincent339 on 2006-03-05
No,I use dhcp,but others not.

---

### Post by darth_vector on 2006-03-05
i take it this isn't your personal network... right?

ask your sysadmin for an un-allocated IP and use a static IP; or suggest he enforce the use of DHCP or of controlled static IP allocations.

---

