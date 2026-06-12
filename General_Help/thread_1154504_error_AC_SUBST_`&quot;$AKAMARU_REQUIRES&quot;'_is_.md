---
title: "error: AC_SUBST: `&quot;$AKAMARU_REQUIRES&quot;' is not a valid shell variable name"
date: 2009-05-09
forum: General Help
---

### Post by DracoJesi on 2009-05-09
what am I missing?

---

### Post by DracoJesi on 2009-05-09
error from kiba dock...

---

### Post by WalmartSniperLX on 2009-09-12
I have no idea. A simple google brought me to this thread because I'm having the same issue in my zenwalk install. If I find the answer/fix, ill make sure to post it here.

---

### Post by thepossiblehuman on 2009-09-17
Go into the config.in and on line 51 change it to say:  AC_SUBST(AKAMARU_REQUIRES)

---

### Post by LordDelta on 2010-01-25
The above fix works for me.

---

