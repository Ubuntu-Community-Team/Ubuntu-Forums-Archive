---
title: "Problem with desktop effects"
date: 2009-03-17
forum: Desktop Environments
---

### Post by ironhorse2008 on 2009-03-17
I using ubuntu 8.10. after I enabled filter in Compiz utility, when I click in my desktop anywhere, shown black screen. I can not do anything, I new in Ubuntu. Pls. advise me how to disable or uninstall compiz step by step ASAP. :confused::confused:

---

### Post by Forlong on 2009-03-17
In case you're on GNOME, here's how to disable Compiz from the command line ([Ctrl]+[Alt]+[F1])
```
gconftool-2 -s -t string /desktop/gnome/session/required_components/windowmanager metacity
```

---

