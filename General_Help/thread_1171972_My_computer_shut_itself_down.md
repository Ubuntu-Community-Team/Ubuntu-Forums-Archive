---
title: "My computer shut itself down?"
date: 2009-05-27
forum: General Help
---

### Post by Nintendo01 on 2009-05-27
I just came home from work and found my computer turned off, and I didn't do it. Everything else on the power strip was still working and not blinking, so it wasn't a power failure. Is there any way to look back in a log somewhere to see what time the computer powered off and possibly why? I don't think anyone in my family would have messed with it, so I want to know what happened.

Also, looking through the various logs in /var/log I couldn't find a reason for the shutdown, but I did discover that there is a cron job running update-motd as root every 10 minutes at exactly 10:01, 20:01, (mm:ss) etc past the hour. What does this do and how can I see what other cron jobs might be running?

Thanks.

---

