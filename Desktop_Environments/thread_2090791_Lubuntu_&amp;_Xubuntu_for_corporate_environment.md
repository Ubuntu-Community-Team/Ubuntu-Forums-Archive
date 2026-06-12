---
title: "Lubuntu &amp; Xubuntu for corporate environment"
date: 2012-12-03
forum: Desktop Environments
---

### Post by uzumakifahim on 2012-12-03
I'm looking for to know about the benefits, problems, friendliness; anything about Lubuntu and Xubuntu in corporate environment. 


[LIST=1]
[*]Is Xubuntu and Lubuntu ready for large corporate implementation?
[*]What could be the problems?
[*]What could be the benefits?
[/LIST]
Any suggestion, experience, tips would be highly appreciable.

Thanks in advance.

---

### Post by sudodus on 2012-12-03
This is interesting also for people who want to do basic things (and only use a few application programs, mainly the web browser, file browser and office software).

I think it is important to use an LTS version to avoid too frequent major updates. Xubuntu 12.04 has 3 years LTS. Unfortunately Lubuntu 12.04 has a normal support period (18 months). It is also important that the application programs are good enough and not too frugal.

I like Lubuntu because it is so light-weight and fast not only for aging computers. But I add xubuntu-desktop (and a few more packages) in order to get what I need. But comparing these flavours out of the box I would suggest Xubuntu for corporate environments.

---

### Post by LewisTM on 2012-12-03
I know large corporations have lots of network shares (mostly Windows/Samba). Xubuntu's Gigolo would work great here by bookmarking these locations and handling automatic connections at login. There is no other tool quite like it.

The downside is the name. Using an app named after a male prostitute is not very corporate friendly. Maybe one could ask the makers of Xfce to package it under a new name for corporate environments.

Cheers!

---

### Post by uzumakifahim on 2012-12-03
@LewisTM, Isn't it possible to use Samba on Lubuntu, other than Gigolo? Though you said Gigolo is good enough. Just want to know is it possible or not?

---

### Post by LewisTM on 2012-12-03
Of course it's possible. Gigolo is just an interface. Its main selling point is to autoconnect to network shares at login, when the network becomes available, something no other tool can do. Windows has had that feature (map network drive at logon) for decades. 

By default, Ubuntu only lets you manually connect to network shares. Many people, and some software, expect networked files to be available right away. The other solution, Samba shares in fstab, is not an option in multiuser environments.

---

