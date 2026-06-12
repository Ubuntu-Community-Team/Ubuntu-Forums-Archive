---
title: "Where does LibreOffice keep logs?"
date: 2013-06-07
forum: Desktop Environments
---

### Post by vadimkolchev on 2013-06-07
I wonder where LibreOffice keeps its logs in Ubuntu. It keeps crashing randomly for me - graying out and closing at different times, so I want to find out why this is happening. It may not crash for a couple of days, that's why it is not a good idea to start it from terminal and wait. So I need to know if there are any logs about LibreOffice crashes. Could anyone help me?

---

### Post by Buntu Bunny on 2013-06-07
You could try a backtrace. After it crashes

```
 bt <enter>
```

---

### Post by vadimkolchev on 2013-06-07
what package provides this binary?

---

### Post by Buntu Bunny on 2013-06-07
libreoffice-dbg

It's in Synaptic.

---

### Post by vadimkolchev on 2013-06-07
Ok, thank you, this is helpful.

---

