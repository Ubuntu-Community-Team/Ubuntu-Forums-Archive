---
title: "Beryl shows blank windows"
date: 2007-02-15
forum: Desktop Environments
---

### Post by vav on 2007-02-15
Hi,

I run MATLAB on my ubuntu machine. When I use Beryl though, the matlab window pops up and shows nothing inside - just grey. When I switch to metacity, the window shows properly!

Why could this be?

---

### Post by Lucretia on 2007-02-18
I get the same thing. Apparently it's a memory problem.

With the newest version of Beryl there is some kind of fix for it. When playing around with the settings, I managed to fix it, but then I messed around with the settings again and the problem came back...

So my advice is get the newest version and mess around with settings...

---

### Post by phoqueyoo on 2007-02-18
Is MATLAB a java program? If it is there is a simple fix for it. Just run:
export AWT_TOOLKIT=MToolkit
befora you start it.

---

### Post by vav on 2007-02-26
> **phoqueyoo said:**
> Is MATLAB a java program? If it is there is a simple fix for it. Just run:
export AWT_TOOLKIT=MToolkit
befora you start it.

Thanks phoqueyoo, that worked.

---

