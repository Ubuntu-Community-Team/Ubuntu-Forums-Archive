---
title: "How to add more repositries??"
date: 2009-04-23
forum: General Help
---

### Post by mubbashar on 2009-04-23
please tell me how to add more repositries in ubunto???

---

### Post by ubu-for on 2009-04-23
Go to "System - System Administration (or similar) - Update Administration (or similar) - Preferences - Third Party Software (or similar) - Add ..."

Or edit your sources.list at "/etc/apt/".

P.S. I'm sorry, if the terms aren't accurate but I only have the German version and had to translate them.

---

### Post by Kain000 on 2009-04-23
the above post is correct, you just need the souce http address to put into it.  that is generally given to you on the repos webpage.

---

### Post by mubbashar on 2009-04-23
please tell me if u know about any repository..

---

### Post by ubu-for on 2009-04-23
Do you mean some additional repositories?

---

### Post by mubbashar on 2009-04-23
yes

---

### Post by drs305 on 2009-04-23
Here is the ubuntu wiki on repositories that should answer most of your questions. I updated it for the most recent LTS (Hardy) but things haven't changed much since then:
[_https://help.ubuntu.com/community/Repositories/Ubuntu_]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by ubu-for on 2009-04-23
> **mubbashar said:**
> yes

```
## MEDIBUNTU (more video codecs)
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

## WINE (run and install Windows programs)
deb http://wine.budgetdedicated.com/apt jaunty main

## VLC 1.0 (best media player)
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
```

---

