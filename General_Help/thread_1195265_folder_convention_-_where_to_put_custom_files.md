---
title: "folder convention - where to put custom files?"
date: 2009-06-23
forum: General Help
---

### Post by BFG on 2009-06-23
I have a number of non-user specific setup files, which need to be on the local HDD, and can't be inside /home as that is mounted from the NAS

Where to put them?  I know I can put them anywhere, but what are the conventions?

/opt ?

Is there a Ubuntu version of:  [http://www.pathname.com/fhs/pub/fhs-2.3.htm](http://www.pathname.com/fhs/pub/fhs-2.3.htm)

Both static files and simple bash scripts.  Thanks.

---

### Post by VCoolio on 2009-06-23
Maybe [this]("http://www.debianadmin.com/linux-directory-structure-overview.html") helps, although it is a little short. Configs would go in /etc/appname I think; executable scripts in /usr/bin. The /opt folder I think is for applications you want separately installed so it's easier to debug or remove. I have for example an additional window manager in alpha status (E17) there. But I'll happily stand corrected.

---

