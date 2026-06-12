---
title: "Desktop Effects"
date: 2008-04-08
forum: Desktop Environments
---

### Post by Caz'ar Xiladys'varion on 2008-04-08
This is pretty much a fresh install of gutsy. Everything was working fine...was messing around with some themes. Somewhere along the line my desktop effects was disabled, and I couldn't reactivate them. I did some searching on the forum, ran apt-get install xserver-xgl, and now I can reactivate them again. When I did though, everything was incredibly laggy, so I turned it off. But everything is *still* incredibly laggy...even scroll bars...it really sucks. My computer is a pain to just generally use now...any ideas on how to fix? :(

---

### Post by Caz'ar Xiladys'varion on 2008-04-08
Ok so I disabled xgl and that fixed all the lag. Any idea how I can get desktop effects to work again?

---

### Post by Caz'ar Xiladys'varion on 2008-04-08
um...it seemed to have magically fixed itself.

weird =P

---

### Post by qamelian on 2008-04-08
> **Caz'ar Xiladys'varion said:**
> Ok so I disabled xgl and that fixed all the lag. Any idea how I can get desktop effects to work again?
What video card do you have? It might be blacklisted due to issues with the current version of compiz. If so, you might be able to get compiz to run by editing the script at /usr/bin/compiz and adding the line ```
SKIP_CHECKS="yes"
``` after the block of comments at the beginning of the script. Then when you active desktop effects it will not check to see if your card is blacklisted. Be aware though, that blacklisted cards are blacklisted for a reason.

---

