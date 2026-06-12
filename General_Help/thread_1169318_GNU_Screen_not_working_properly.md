---
title: "GNU Screen not working properly"
date: 2009-05-25
forum: General Help
---

### Post by tlb-xeno on 2009-05-25
I used screen once and it worked perfectly. When I tried it the day after it didn't show the status bar in the bottom of the terminal window. The shortcut keys (like F9 for help) doesn't work either.

Does someone have a solution to this problem?

I am using Ubuntu 9.04 and screen version 4.00.03jw4

---

### Post by Vunutus on 2009-05-25
I had this exact same problem the other day and finally someone gave me a solution.

Shut down screen and run

```
select-screen-profile
```

and select your color scheme. Start up screen again and it should be functioning as normal.

---

### Post by tlb-xeno on 2009-05-25
Thanks. Now it works perfectly :)

---

