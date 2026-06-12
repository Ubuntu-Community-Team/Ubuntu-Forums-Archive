---
title: "Gnome-schedule -- Unison problem"
date: 2009-01-21
forum: Desktop Environments
---

### Post by rwigle on 2009-01-21
I have a working unison profile that works fine from the command line with 

```
unison -batch
```

I use gnome-schedule, and have two events set up:

1. (command line above) at reboot
2. (command line above) every hour

If I use "execute task" in gnome-schedule, they work fine, but they don't seem to work otherwise. (???)

My default profile includes a root via ssh, and this seems to be the problem. I have rsa authentication working fine, and Unison is installed on both machines (Ubuntu Hardy 8.04)

One puzzle.. even if I add -auto AND -batch switches, it seems that unison (or gnome-schedule?) wants a [ENTER] to finish... Is that the problem?

Thanks in advance for suggestions.

---

