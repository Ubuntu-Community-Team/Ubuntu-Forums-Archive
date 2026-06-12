---
title: "xCHM doesn't like /etc/mailcap"
date: 2006-09-20
forum: Desktop Environments
---

### Post by MaXiMuS-D on 2006-09-20
Every time I run xCHM, it says "mailcap file /etc/mailcap line 56 incomplete entry ignored". Okay, now what do I do to that incomplete entry? And what does this file do anyways?

Thx in advance :-)

---

### Post by skymt on 2006-09-20
Please post line 56 of /etc/mailcap, and we can help you.

/etc/mailcap is one (old) method used to associate filetypes with applications.

---

### Post by MaXiMuS-D on 2006-09-21
Here's line 55 and 56 -

55 - application/x-cgwdtheme
56 - ext:cgwdtheme

So what's the problem?

---

### Post by skymt on 2006-09-21
Delete both lines. They don't do anything.

Or, if you happen to know what application uses application/x-cgwdtheme, you can replace line 55 with:```
application/x-cgwdtheme;  i-open-cgwd-themes %s
```

---

### Post by stani on 2006-09-30
I have almost exactly the same problem. My lines are:
```
55 application/x-emerald-theme
56	ext: emerald
```
When I union these two lines the problem disappears. But next time I restart my computer the trouble starts again.Is this a bug in Ubuntu which should be filed?

I'm on Edgy.

Stani

---

### Post by zhouray on 2006-12-09
I have the same problem too, after installing Beryl. So, no fix?

---

### Post by hikaricore on 2006-12-09
One of your packages is fudging up the mailcap file.  I don't think this problem has anything to do with a ubuntu bug.

---

