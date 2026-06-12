---
title: "Terminal Console"
date: 2005-12-19
forum: Desktop Environments
---

### Post by sillyme on 2005-12-19
Hi all,

I have Ubuntu installed on my PC notebook. I want to use it as a terminal console to other headless servers. I've tried using getty <getty -L ttyS0 9600 vt100>, but so far I cannot get it to work. I wasn't able to get a prompt.

How do I go about configuring the tty settings? Is there other alternatives to getty?

---

### Post by LucidParody on 2005-12-19
ssh?

```
man ssh
```

---

### Post by sillyme on 2005-12-19
ssh doesn't work. I need serial connection through COM1.

---

