---
title: "Ubuntu 6.10 + Cedega 5.2.3 = problems?"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by LordBug on 2006-10-28
(Cross-posted to TransGaming as well)

I re-formatted and did a fresh install of 6.10 last night.  Installed Cedega 5.2.3 via their .deb download.  Now whenever I try to have Cedega get updates from TransGaming, the program just freezes.  I have to kill it.  Running from a console yields no error messages at all.  Everything else in 6.10 is working perfectly.

Anyone else tried Cedega with 6.10 yet?

---

### Post by Perfect Storm on 2006-10-28
Works fine here...

---

### Post by NeoRazorX on 2006-10-28
To update Cedega:

[INDENT]sudo dpkg-reconfigure dash[/INDENT]

And select NO.

But i have a problem with excesive speed on Cedega. Need for Speed: Most wanted is extremely faster, i can't play :(

---

### Post by dahli.llama on 2006-10-30
The excessive speed can be caused by powernowd being enabled.  I know I have to get rid of that on my AMD64 system or I have all kinds of problems.

---

### Post by drews_blunted on 2006-10-31
i had the same problem with my install of cedega. Go ahead and get the local update from the transgaming page. unselect check the internet for updates. and install from local update. This should fix the problem. After that cedega should set itself up correctly. 

Furtherwise i have noticed some slowdown in cedega in edgy aswell as the fact that it has problems with beryl/XGL

---

### Post by handy on 2006-10-31
I have no problems playing Guild Wars with Cedega & Edgy.

---

### Post by Perfect Storm on 2006-10-31
> **drews_blunted said:**
> i had the same problem with my install of cedega. Go ahead and get the local update from the transgaming page. unselect check the internet for updates. and install from local update. This should fix the problem. After that cedega should set itself up correctly. 

Furtherwise i have noticed some slowdown in cedega in edgy aswell as the fact that it has problems with beryl/XGL

Beryl/xgl/aiglx slows down 3D gaming. So if people are ultra gamer and want their OS to perform the best, beryl and the like is not recommended.

---

### Post by frodon on 2006-10-31
I'm fine with edgy and cedega as well.

---

### Post by LordBug on 2006-10-31
> **NeoRazorX said:**
> To update Cedega:

[INDENT]sudo dpkg-reconfigure dash[/INDENT]

And select NO.

Got this reply on the TransGaming forums too.  It worked, and is definitely not something I would've thought of.

---

