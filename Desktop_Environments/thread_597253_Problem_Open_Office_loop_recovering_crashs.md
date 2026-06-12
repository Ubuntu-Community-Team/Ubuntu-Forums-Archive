---
title: "Problem: Open Office loop recovering crashs"
date: 2007-10-30
forum: Desktop Environments
---

### Post by lugburz on 2007-10-30
My open office installation stopped to work. Any time that I try to run one of the programs but the crash recovering window appears, it try to recover I file that never crashed and then OO doesn't appear anymore.

Someone know the reasons?

---

### Post by por100pre1 on 2007-10-31
Try this commands in Terminal:

```
pkill soffice
```

```
mv .openoffice.org2 .openoffice.org2_backup
```

Then restart OOo. Hope it helps. Sorry for the delay.

---

### Post by lugburz on 2007-11-05
> **por100pre1 said:**
> Try this commands in Terminal:

```
pkill soffice
```

```
mv .openoffice.org2 .openoffice.org2_backup
```

Then restart OOo. Hope it helps. Sorry for the delay.

I tried but then I found that the problem is related to a change of  aspect. so I restored for ubuntu the human theme and this fixed the problem.

A stupid but important bug that someone will have to solve. :(

---

### Post by por100pre1 on 2007-11-05
> **lugburz said:**
> I tried but then I found that the problem is related to a change of  aspect. so I restored for ubuntu the human theme and this fixed the problem.

A stupid but important bug that someone will have to solve. :(

Did you use other theme when you faced the issue? By the way, I'm glad to know you fixed the issue. :)

---

### Post by lugburz on 2007-11-06
I used OO impress for some days while I had the deafault theme, then I customized the theme: using tthe crux theme, default icons... this seems break oo impress.

---

### Post by por100pre1 on 2007-11-07
> **lugburz said:**
> I used OO impress for some days while I had the deafault theme, then I customized the theme: using tthe crux theme, default icons... this seems break oo impress.

Thanks for letting me know. :) This could be a bug. :-k

---

