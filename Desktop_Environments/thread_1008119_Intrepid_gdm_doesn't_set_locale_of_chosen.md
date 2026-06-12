---
title: "Intrepid gdm doesn't set locale of chosen"
date: 2008-12-11
forum: Desktop Environments
---

### Post by WatsonJX on 2008-12-11
Hi all,

Just installed Intrepid, and found that whatever language I choose at gdm login options, it set the $LANG to "C". I put "echo $LANG" in /etc/gdm/Xsession so I know that $LANG is "C" from very beginning to the end.

This is gdm 2.20.8-0ubuntu. Before repro this, I removed file /etc/default/locale, removed any locale variables in /etc/environment to avoid side effect.

On my old desktop it works well, gdm version is 2.20.5-0ubuntu.

Any clue?

Thanks.

---

