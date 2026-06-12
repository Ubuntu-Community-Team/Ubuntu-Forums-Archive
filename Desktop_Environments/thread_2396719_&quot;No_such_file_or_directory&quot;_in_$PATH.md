---
title: "&quot;No such file or directory&quot; in $PATH"
date: 2018-07-19
forum: Desktop Environments
---

### Post by sunbear-c22 on 2018-07-19
I noticed a `No such file or directory` statement in my $PATH after login which is irregular. 

```
$ $PATH
bash:$HOME/.pyenv/shims:$HOME/.pyenv/bin:$HOME/bin:$HOME/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin: No such file or directory



```

How do I discover which application startup process is causing it?

---

### Post by deadflowr on 2018-07-19
That's just the command doing that.
run echo $PATH and it won't show the no such stuff.

look at here:
[https://superuser.com/questions/881463/no-such-file-or-directory-after-typing-path-in-terminal]("https://superuser.com/questions/881463/no-such-file-or-directory-after-typing-path-in-terminal")
for a simpler/better explanation than i could give.

---

### Post by sunbear-c22 on 2018-07-20
Thanks. My bad. Issue resolved.

---

### Post by mIk3_08 on 2018-07-20
sunbear-c22 if this thread already solve. Please mark it as solve. Thanks a lot. Good Luck.

---

### Post by geeksquad12345 on 2018-07-20
such a important post for me thank you

---

