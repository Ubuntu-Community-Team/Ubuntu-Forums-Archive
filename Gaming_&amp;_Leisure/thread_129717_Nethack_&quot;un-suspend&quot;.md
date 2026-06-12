---
title: "Nethack &quot;un-suspend&quot;?"
date: 2006-02-14
forum: Gaming &amp; Leisure
---

### Post by James_Nostack on 2006-02-14
I've been playing a bit of Nethack lately, and keep accidentally hitting Ctrl+Z, which suspends the current game, kicking me back into the shell.  How can I get back to a game that's been suspended?

My apologies for asking what must be a pretty common question.  I've looked through the on-line help manual but haven't been able to spot the solution.  

best,
James

---

### Post by lleonard on 2006-02-14
[QUOTE=James_Nostack]I've been playing a bit of Nethack lately, and keep accidentally hitting Ctrl+Z, which suspends the current game, kicking me back into the shell.  How can I get back to a game that's been suspended?
[/QUOTE]

fg

---

### Post by engla on 2006-02-14
If you have many "jobs" suspended in one term, 'fg' puts the last one in the foreground. You can also type 'jobs' to get a list of them and then use %N where N is the jobnumber. Or you can use 'bg' or %N & to resume a job, but in the backround.

---

### Post by James_Nostack on 2006-02-14
thanks very much!

---

### Post by lleonard on 2006-02-14
Oh yeah, since you're nethacking, that's fg for foreground not your pet cat attacking a gremlin. :-)

---

