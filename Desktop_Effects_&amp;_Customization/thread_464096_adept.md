---
title: "adept"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by Pyranima on 2007-06-04
maybe someone here can help me adept manager crashed on me and now its locked. i cant delete the locked file and i cant kill apt of any kind. HELP

---

### Post by nereid on 2007-06-04
Is adept still running? Then you have to kill adept itself. You do have checked all running processes?

```

ps ax

```

Should give you a list of all running processes, search for anything that might block the apt database (aptitude, apt-get or adept) and kill these processes either with *kill <pid>* or *killall <name>*.

---

