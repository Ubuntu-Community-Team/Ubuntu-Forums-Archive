---
title: "HELP! error which i dont know how to get rid of =["
date: 2009-03-07
forum: General Help
---

### Post by H0RIZ0Ns on 2009-03-07
Heyy everyone, i dont understand why but on some of my programs text shows as dots instead of text, the main programs it happens on is Amarok music player, and Rosegarden.

i was wondering if anyone knows how to fix this problem cause its really annoying me now =[

i've tried taking screenshots but for some reason it hasnt worked

Thank you
  H0RIZ0Ns

---

### Post by LoneWolfJack on 2009-03-07
open a terminal window an type

```
echo $LANG
```

if it doesn't say UTF-8, you're probably trying to display characters that are not in your current charset.

---

### Post by H0RIZ0Ns on 2009-03-07
It is UTF-8   

any other idea's ?

---

