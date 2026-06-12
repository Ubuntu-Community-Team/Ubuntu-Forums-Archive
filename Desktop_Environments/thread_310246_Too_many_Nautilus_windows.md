---
title: "Too many Nautilus windows"
date: 2006-11-30
forum: Desktop Environments
---

### Post by shochatd on 2006-11-30
I'm running 6.10/Edgy. Recently a strange thing started happening. When I log in, I get a bunch of Nautilus windows even though there were none open when I logged off. Even stranger, when I try to bring one up using Places->Home Folder, I get not just one, but sometimes as many as 6 Nautilus windows opening. How can I fix it so that I don't get any when I log in, and I just get one when I request one?
-- David

---

### Post by swamytk on 2006-12-02
Just rename ~/.gnome2/session as session.bak or remove it. logout and login.

---

### Post by shochatd on 2006-12-02
Thank you! That cured the problem. I was on the verge of making a new empty home directory, but your less severe method means much less work.

---

