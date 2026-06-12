---
title: "Huge window titlebar with compiz????"
date: 2007-11-10
forum: Desktop Environments
---

### Post by petew00 on 2007-11-10
Hi,

Since installing Gutsy I have sometimes the problem that when I start my PC the window titlebars are huge. Can't detect the particular circumstances that inflict this problem. I solve it by temporarily disabling the compiz eye candy (and then re-enable it).

Enclosed are two screenshots: the first with the huge titlebars, the second with normal titlebars.

Can anybody help me with this? What could be the problem?

PS: My portable PC is a Dell Precision M65 with NVIDIA card.

---

### Post by pedrogl on 2007-11-10
Hi, edit /etc/gdm/gdm.conf-custom and add the following:
```
[server-Standard]
command=/usr/bin/X -br -audit 0 -dpi 96
```

Change the "96" to the same value that appears on System->Appereance->Fonts->Details->Resolution

I can't remember where I found that tip, but it worked for me.

---

### Post by petew00 on 2007-11-11
Thnx pedrogl! 

I also found that post. It solved the problem! This is the link to the post:

[http://ubuntuforums.org/showthread.php?t=583915](http://ubuntuforums.org/showthread.php?t=583915)

---

