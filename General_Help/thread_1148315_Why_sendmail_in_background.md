---
title: "Why sendmail in background?"
date: 2009-05-04
forum: General Help
---

### Post by zoomiest on 2009-05-04
Just a quick question... I see sendmail being left to run in the background on every Linux installation I have ever seen. 

Need I leave it there? Is this use of sendmail, to facilitate my own mailto: links or something? (talk about self-reliance...)

Why is it there? May I take it out to conserve memory?

---

### Post by cmnorton on 2009-05-04
Usually the system needs to send you mail. Maybe that's just in the case of configuring an Ubuntu system to be more workstation/server-like rather than as a pure desktop client. I have never experimented with not having sendmail running and getting any emails (like from logwatch). 

If you are strictly set up as a desktop and you will always log into an email server or use web-based email, then you could certainly try to live without it, but I would not uninstall it. To stop sendmail from running, instead of un-installing it, as root, you'd use update-rc.d to turn sendmail's runlevels off. 

For the little amount of ram its using, I'd leave it running. If you tweak sendmail's config with a SMART host, your Ubuntu box can send mail using your email server, as long as port 25 is not blocked.

---

