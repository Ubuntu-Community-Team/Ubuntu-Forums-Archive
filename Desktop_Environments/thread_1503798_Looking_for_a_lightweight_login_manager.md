---
title: "Looking for a lightweight login manager?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by dsavi on 2010-06-07
So I have this ancient laptop that is running Ubuntu (Lucid), and I'd like to use a login manager that's more lightweight than GDM. This isn't the first place I came, I have googled this. First I timed a boot with GDM, which went fine, a bit over 43 seconds (Not bad considering this thing has a 366mHz processor and 256mb of RAM). Then I installed SLiM, rebooted, and got nearly ten seconds more. I rebooted again (You can't really tell from the first boot IMO) and I got a few seconds less. This occurs to me as strange, as I was under the impression that GDM was a lot heavier than SLiM. I have also tried XDM, but it doesn't have the features that I need (Session switching). Is there some other obscure display/login manager that I haven't tried? Will changing the GDM theme to something more lightweight work? Looking forward to hearing your replies.

---

### Post by Zemblan on 2010-06-07
I'd imagine there are many factors other than the boot manager which have a more significant effect on your boot time.

---

### Post by dsavi on 2010-06-07
Yes, I have already gone through my startup services with sysv-rc-conf; However, in this case, the login manager was the **only thing** that I changed. It was literally on the boot before I installed SLiM that I timed GDM, and one reboot later that I timed SLiM.

---

