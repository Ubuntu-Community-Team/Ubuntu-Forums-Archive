---
title: "Checking Ubuntu Unity"
date: 2011-12-09
forum: Desktop Environments
---

### Post by aishsarathy on 2011-12-09
Hi,

Is there a way to check through the command line if I'm running Ubuntu Unity or not ?

---

### Post by Lars Noodén on 2011-12-09
You can use [ps](http://manpages.ubuntu.com/manpages/precise/en/man1/ps.1.html) and [grep](http://manpages.ubuntu.com/manpages/precise/en/man1/grep.1posix.html).

```

ps x | grep unity

```

That will show you if you are running any processes with 'unity' in the name.  If you are running Unity, then there should be quite a few processes to see.

---

### Post by Frogs Hair on 2011-12-09
To find out if your computer is Unity 3D compatible use the command below .

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by marinara on 2011-12-09
i had the same problem.  I ended up posting screenshots to the forum and people still couldn't decide

---

