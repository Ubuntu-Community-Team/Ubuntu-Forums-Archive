---
title: "Spamassassin spamd eating up memory"
date: 2005-06-14
forum: Desktop Environments
---

### Post by biodiesel-bri on 2005-06-14
Hi all-

Any ideas why spamd had 19 processes eating up almost 20% of my 786mb of my RAM?  That seems rather excessive.  I did a 'killall spamd' and with one mail check spamd is back to eating 17% of my RAM.

Ok, I quit Evolution and restarted and that seems to have helped but you'd think Evolution would let go of all those spamd proceses.

Thanks,

-B

---

### Post by Akoluth of Nandus on 2005-06-14
I know this problem and I have no real solution but a workaround that may be suitable for you.

Open gconf-editor and go to "/apps/evolution/mail/junk/sa". There is a key "use_daemon". Set it to false and Evolution will use spamassassin instead of spamd.
This will slow down the filtering process but spamassassin will only run when it actually filters messages.

---

