---
title: "Frostwire Issues"
date: 2006-04-12
forum: Desktop Environments
---

### Post by bluemike807 on 2006-04-12
I've installed Frostwire - the Limewire counterpart - and Im having trouble getting it to run. As far as I can tell the install itself was complete and whole; there's an icon under App's>Internet, but clicking it does nothing whatsoever, no process spawns.

I have, I think, the latest JRE - I downloaded and installed it to the best of my ability (I followed instructions I found in this forum, linked against the installation of Frostwire itself). But no dice.

Can someone please point me down the path of at least diagnosing what is going wrong? Thanks

---

### Post by Ramses de Norre on 2006-04-12
Can you run it from terminal and check for error messages?

---

### Post by taurus on 2006-04-12
I bet you 10 to 1 it has everything to do with the dos2unix thing!  But will wait to see the error message from a terminal first...  ;)

---

### Post by bluemike807 on 2006-04-12
michael@leosubuntu:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()

---

### Post by jrib on 2006-04-12
```
sudo aptitude install sysutils && sudo dos2unix /usr/lib/frostwire/runFrost.sh && frostwire
```

(after that you can run frostwire normally)

---

### Post by anemptygun on 2007-09-26
Mine is doing the same thing. I'll try this out, I hope it works.

thanks

---

