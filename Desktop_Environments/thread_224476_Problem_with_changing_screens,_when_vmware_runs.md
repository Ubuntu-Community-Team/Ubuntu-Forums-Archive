---
title: "Problem with changing screens, when vmware runs"
date: 2006-07-28
forum: Desktop Environments
---

### Post by big.EdE on 2006-07-28
Hi!

When I used pure Debian, I was able to switch to vmware's screen through Ctrl+Alt+F8 (or F9, if two X servers was running), and back to Debian's X through Ctrl+Alt+F7.
On Ubuntu tty8 is used for startup messages, so vmware seems to use next tty9. It seems to, because when I switch to it, X hooks up with some random graphic output. The only thing I can do to connect remotely to my notebook and restart X (or ugly reset).
I know, fullscreen on vmware can be enabled by Ctrl+Alt+Enter (and back with Ctrl+Alt), but this bug is annoying. Sometimes, when I forget about it, and try to quick-switch to vmware's screen by switching screens, I end up with locally unusable notebook.

Any ideas, what should do this?
thx

EdE

---

### Post by bigken on 2006-07-28
Have you installed vmware tools ;)

---

### Post by big.EdE on 2006-07-28
No, hadn't.. I run Solaris in vmware, and I didn't succeed in installing UNIX vmware tools in it..
Anyway, on Debian I hadn't these tools eather, so this can't be the problem..

---

