---
title: "Dell XPS 1530--Hibernate disappeared + action forbidden"
date: 2008-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slabix on 2008-06-23
Hibernate has just disappeared from my power options. In addition when I use the Dell keyboard shortcut Fn+F1 (just out of curiosity, not because I was expecting it to work), I get a message "Action Forbidden Hibernate is not available on this computer."

As near as I can tell, this all happened as a result of using EnvyNG to activate my NVIDIA 8700 GT driver.

Suspend seems to be working fine-ish. There are some weird display flashes and oddness, but it's OK.

My apologies if this has been handled elsewhere in the forums--I swear I searched.

---

### Post by slabix on 2008-06-24
Forgive me again if I'm stating something so pointless that it doesn't bear saying, but I'm a noob, and you know how we do. ..

Anyway, to answer my own thread, when suspend also became dodgy and my machine felt like it was running so hot that it was going to melt the table, I broke down and did a different installation.

Noob that I am, I had installed 8.04 using Wubi to dual boot with Vista (so as not to void my warranty according to Dell support), and as far as I can tell, that was the source of 90% of my problems with the m1530.

Re-installed in its own dedicated partition, rather than embedded in Vista, my fan and temperatures are back to normal, I have real sleep and hibernate, and my dual processors appear to be doing what they're supposed to.

So I'm probably stating the (very) obvious, but it seems to me that Wubi is a great way for newbies to sameple, but things won't ever be right in a dual boot using it. Is that right?

---

