---
title: "Resume from suspend issue"
date: 2009-06-06
forum: Desktop Environments
---

### Post by cochran242 on 2009-06-06
I am having an issue when resuming from suspend in Ubuntu 9.04. It worked for a few weeks, but now when I resume it prompts for me to login, and when I do I am in a NEW session instead of resuming my old session. Anyone with any ideas?

---

### Post by kerry_s on 2009-06-06
check your /var/log/pm-suspend log, sounds like your X is crashing to me.
do you have effects turned on?

---

### Post by cochran242 on 2009-06-07
Thanks Kerry! you were right on the money! I looked in the log you suggested but I found no errors but yes, I did have effects turned on. I have a blacklisted card Intel GM965/GL960 with compiz and I added SKIP_CHECKS=yes so I could still use compiz. Guess I will remove that. Thanks again.

---

