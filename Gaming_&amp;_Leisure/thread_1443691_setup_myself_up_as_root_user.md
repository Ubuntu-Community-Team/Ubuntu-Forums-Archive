---
title: "setup myself up as root user"
date: 2010-03-31
forum: Gaming &amp; Leisure
---

### Post by jbumgar on 2010-03-31
I need to run as root to fully remove crossover games but when i type in su it asks me for my pwd so i typed in my user pwd but it said Authentication failure.  How do i set myself up as a root?

---

### Post by sisco311 on 2010-03-31
By default, the root account password is locked, so you can't use su or login directly as root.

But, you can use sudo to run an application as root:
```
sudo command
```
sudo prompts you for your user password. 

Take a look at the community documentation: [uhelp]community/RootSudo[/uhelp]

---

