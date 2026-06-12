---
title: "Software Center problems"
date: 2010-02-27
forum: Desktop Environments
---

### Post by BlacqWolf on 2010-02-27
Hello. I have had a new PC for about 2 months, and whenever I installed Ubuntu 9.10 on any machine, I noticed software center somehow worked after I installed Adobe Flash for Firefox. But now, I installed it on my new notebook and it will repeatedly say "Unavailable in the current data" or "Not available for your hardware architecture" and I cannot download anything. I used to somehow fixed this just with install of Adobe Flash, but now it wont go away. I've been on the web for about 3 hrs looking for a solution and nothings worked. Any ideas?

---

### Post by Kakers on 2010-02-27
type in a terminal window:

```
sudo apt-get update
```

If that doesn't work:

```
cat /etc/apt/sources.list
```

and copy to here what comes up

---

