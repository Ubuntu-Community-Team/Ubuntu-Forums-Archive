---
title: "Nautilus not starting at login after upgrade to 13.04- corrupt user profile?"
date: 2013-04-27
forum: Desktop Environments
---

### Post by danep on 2013-04-27
I just upgraded from 12.10 to 13.04. Immediately after the upgrade, when I log in, no desktop icons are shown and I can't right-click on the desktop. If I manually start nautilus, then the desktop appears properly.

I can't figure out why nautilus is not starting. I don't see anything unusual in syslog when I log in. I created a new user account, and it does not have this problem, so I'm thinking something in my user account related to nautilus must be screwy.

The only thing out of the ordinary during the upgrade was a notice about replacing a gnome defaults file, I think.

Can anyone help me track down the problem, or come up with a workaround?

---

### Post by danep on 2013-04-28
Turns out the problem was with a startup script. I'm not sure why it just started misbehaving after the upgrade, but I guess that's a separate issue.

---

