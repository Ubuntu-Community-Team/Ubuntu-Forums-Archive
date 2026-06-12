---
title: "Help with Virtualbox Enable Passthrough"
date: 2008-11-04
forum: Desktop Environments
---

### Post by wah fun on 2008-11-04
I have virtualbox 2.0.4 with an XP host and ubuntu 8.04 guest installation. Everything works great except brasero cannot see my cd drive, so I cannot burn a cd. I have installed linux guest additions and understand that the cd/dvd passthough option should allow the guest to see the CD/DVD drive. However, when I enabled passthrough in the VM setup, I cannot start the VM. I get an error: vbox status code -38(VERR_ACCESS_DENIED).

Thx

---

### Post by jdpearson on 2008-12-28
> **wah fun said:**
> I have virtualbox 2.0.4 with an XP host and ubuntu 8.04 guest installation. Everything works great except brasero cannot see my cd drive, so I cannot burn a cd. I have installed linux guest additions and understand that the cd/dvd passthough option should allow the guest to see the CD/DVD drive. However, when I enabled passthrough in the VM setup, I cannot start the VM. I get an error: vbox status code -38(VERR_ACCESS_DENIED).

Thx

I have the same issue with v. 2.1  Here's what I found:

[http://www.virtualbox.org/ticket/2795](http://www.virtualbox.org/ticket/2795)

and

[http://forums.virtualbox.org/viewtopic.php?t=12642&highlight=passthrough](http://forums.virtualbox.org/viewtopic.php?t=12642&highlight=passthrough) which suggests downgrading to 2.06

---

