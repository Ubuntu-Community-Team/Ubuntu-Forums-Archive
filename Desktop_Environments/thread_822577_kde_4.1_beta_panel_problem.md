---
title: "kde 4.1 beta panel problem"
date: 2008-06-08
forum: Desktop Environments
---

### Post by funnypanks on 2008-06-08
i installed kde 4.1 beta 1. and whenever i add a widget to the panel, it seems to span the entire panel. so if i add a clock the entire panel becomes the clock. if i add notification area all the notification icons are there, just spread across the entire bar. is there some way to creat seperators to limit the size of widgets?

---

### Post by GeneralZod on 2008-06-08
> **funnypanks said:**
> i installed kde 4.1 beta 1. and whenever i add a widget to the panel, it seems to span the entire panel. so if i add a clock the entire panel becomes the clock. if i add notification area all the notification icons are there, just spread across the entire bar. is there some way to creat seperators to limit the size of widgets?

Sounds like a bug - there are widgets that give hints to the panel that they should grab as much free space as possible, but the clock probably isn't one of them :)

File a bug report at bugs.kde.org, including screenshots and your plasmarc and plasma-appletsrc (can't remember the exact names of the files at the moment).

---

### Post by Darkdelusions on 2008-06-08
This indeed is a bug. I installed the packages last night and experienced the same issue. Also my friend complied his by source and is also see the panel issues. 

However the panel so far is the only bug i have found so far... Well that and the Kmenu icons

---

