---
title: "Pidgin to Adium using the Bonjour protocol"
date: 2009-03-20
forum: General Help
---

### Post by Yashiro on 2009-03-20
Background:
machine1: 8.04 LTS running Pidgin 2.5.5
machine2: iMac and Adium with all latest updates.

Problem:
We can chat and see each other fine over the Lan but file transfers do not work. 
The transfer is started by the sender but no dialog appears on the receivers machine no matter which client starts it.

Given Pidgin and Adium share the same back end I was especially surprised that this did not work. Is this a known broken feature or are there some administrative hoops I need to jump through? (which defeats the point of zeroconf I guess, heh)

Hard file sharing is one of the most oft-recurring issues and is always high on Brainstorm.
Getting cross platform bonjour transfers working is surely easier and better than trying to port something like Giver.

---

### Post by Yashiro on 2009-03-24
No-one else running a Lan with mixed clients?

---

### Post by jfthuong on 2010-09-24
> **Yashiro said:**
> No-one else running a Lan with mixed clients?

I have the same problem between Adium and Pidgin. Haven't found a solution yet but found this link that may be a lead:

[http://trac.adium.im/wiki/FileTransfer](http://trac.adium.im/wiki/FileTransfer)

> **Improving Bonjour file transfer[ ¶]("http://trac.adium.im/wiki/FileTransfer#ImprovingBonjourfiletransfer")**

  For Bonjour file transfer to work when sending it is required to allow port 5298 TCP and UDP in. 


Haven't managed to allow the TCP and UDP port yet though.

---

