---
title: "Can I stop auth.log recording CRON entries?"
date: 2009-05-09
forum: General Help
---

### Post by Fynn on 2009-05-09
Hi,

My auth.log file is filling up with entries relating to a CRON job which runs every 5 minutes.  Could anyone tell me if it's possible and/or desirable to exclude these from logging?

```

May  9 19:55:01 liverpool CRON[27188]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 19:55:01 liverpool CRON[27188]: pam_unix(cron:session): session closed for user root

```

Thanks

---

