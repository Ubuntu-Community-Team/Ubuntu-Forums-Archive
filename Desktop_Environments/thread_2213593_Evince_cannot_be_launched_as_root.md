---
title: "Evince cannot be launched as root"
date: 2014-03-27
forum: Desktop Environments
---

### Post by actionmystique on 2014-03-27
Hello,
On **ubuntu 13.10**, if I run evince with "**gksu evince**", I get the following error messages:

[I]** (evince:5860): WARNING **: Could not open X display
No protocol specified
Cannot parse arguments: Cannot open display: [/I]

Any suggestion?

---

### Post by bapoumba on 2014-03-27
[http://ubuntuforums.org/showthread.php?t=1651832](http://ubuntuforums.org/showthread.php?t=1651832)
May be there ?

---

### Post by actionmystique on 2014-03-28
Thanks for the link.
One user suggested the following trick in the thread:
[I]sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable
sudo /etc/init.d/apparmor restart[/I]

I don't understand why a symbolic link would solve this case, but it works.

---

### Post by actionmystique on 2014-03-28
A side effect is that the "**save current settings as default**" does not work anymore, as far as the previously loaded page is concerned.
I cannot find the config file for evince.
Do you know how to solve this?

---

### Post by mc4man on 2014-03-28
> **actionmystique said:**
> 

I don't understand why a symbolic link would solve this case, but it works.
It 'works' because that link disables apparmor protection of evince from actions/permissions  it's not intended for or shouldn't need to work

---

