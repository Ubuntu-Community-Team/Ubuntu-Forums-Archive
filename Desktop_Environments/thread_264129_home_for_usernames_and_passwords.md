---
title: "/home/ for usernames and passwords?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by alecjw on 2006-09-24
Where are the usernames and passwords stored? In /home/? Would it be possible to make several computers have the same users by having the /home partition on an nfs server?

---

### Post by kidders on 2006-09-24
Hi there,

Users & passwords are stored in /etc with the rest of your system settings. As you might imagine though, what you want to do is pretty common... here's one way:

Read about LDAP-based authentication. It can be a little bit tricky to get it working perfectly, but once you have, you can make multiple computers authenticate against a single source. With the help of samba (configured to act as a PDC) you can even authenticate Windows/Apple machines against it!

Next, you can decide whether you want all your users to keep the same home, regardless of which computer they're using (think "roaming profile"). That's where NFS comes in.

If this sounds interesting, let me know, and I can try to be more specific.

---

### Post by alecjw on 2006-09-24
Wouldn't it be simpler just to mount /home and /etc from the network? Or is mounting something over /etc/fstab going to confuse it?

---

### Post by kidders on 2006-09-24
That would be the least of your problems if you shared another machine's /etc. My advice would be not to even *think* about trying that! Hehe. It might _perhaps_ be possible to use cron to periodically sync certain /etc files on all your machines, but not unless they're all using exactly the same version of exactly the same Linux and have exactly the same software installed. Even then, it might not work.

I've always found that, even if it's a bit hairy, going with well-known solutions to common problems is the safest course. That way, you know the side-effects are predictable, and that help is only a google search away :-)

There may well be other forms of centralised authentication available that suit you better than LDAP ... have a look around and see what you find. LDAP is extremely widely supported though, especially when it comes to things like web/mail servers ... in case that makes a difference.

---

