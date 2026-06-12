---
title: "Huge window titlebars with compiz????"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by petew00 on 2007-11-10
Hi,

Since installing Gutsy I have sometimes the problem that when I start my PC the window titlebars are huge. Can't detect the particular circumstances that inflict this problem. I solve it by temporarily disabling the compiz eye candy (and then re-enable it).

Enclosed are two screenshots: the first with the huge titlebars, the second with normal titlebars.

Can anybody help me with this? What could be the problem?

PS: My portable PC is a Dell Precision M65 with NVIDIA card.

---

### Post by rainwalker on 2007-11-10
Do you have bigger screenshots? Those two don't expand bigger than the preview

---

### Post by jimerickso on 2007-11-10
go to emerald
go to themes & settings
go to edit themes
go to titlebar
adjust minimum height of titlebar

---

### Post by rainwalker on 2007-11-10
> **jimerickso said:**
> go to emerald
go to themes & settings
go to edit themes
go to titlebar
adjust minimum height of titlebar

That wouldn't work because apparently it varies from session to session

---

### Post by jimerickso on 2007-11-11
oh my bad! sorry about that i misunderstood the post.

---

### Post by petew00 on 2007-11-11
Hi all, 

The problem is solved. I found this link to the solution:

[http://ubuntuforums.org/showthread.php?t=583915](http://ubuntuforums.org/showthread.php?t=583915)

Solution:

1. sudo gedit /etc/gdm/gdm.conf
2. find the section [server-Standard] in that file
3. You should see a line that says "-command=/usr/bin/X -br -audit 0". Change it to read "-command=/usr/bin/X -br -audit 0 -dpi 96".
4. Save, quit, and restart

---

