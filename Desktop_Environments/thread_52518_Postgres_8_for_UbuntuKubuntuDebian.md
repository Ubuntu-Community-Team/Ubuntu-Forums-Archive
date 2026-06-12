---
title: "Postgres 8 for Ubuntu/Kubuntu/Debian"
date: 2005-07-28
forum: Desktop Environments
---

### Post by alquimista on 2005-07-28
Hi,
Using Kynaptic I see that I can download Postgres 7.4, but I need version 8 for some projects I was developing in Win using Postgres 8. Is there a version for Ubuntu/Debian that I can get and if so, how can I do it? In [www.postgresql.org](www.postgresql.org) I found releases just for Red-Hat and Fedora.

Thanx,
Guillermo

---

### Post by johanvdw on 2005-07-28
I tried searching:
[http://www1.apt-get.org/search.php?query=postgresql](http://www1.apt-get.org/search.php?query=postgresql)

Postgresql 8 can be found in debian experimental. It is called "experimental", so ofcourse it can deliver problems and I would only use it for experimention until you are sure that everything works well.

Add:
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) ../project/experimental main contrib non-free
to your sources.

---

