---
title: "scripting in grub.cfg"
date: 2010-11-29
forum: Desktop Environments
---

### Post by alokmahor on 2010-11-29
Hi all,
my grub menu has 5 entries. grub.cfg has line [FONT=courier new]set default="0"[/FONT] i  want to change its value alternately on every restart from 0 to 4 and 4  to 0 . so I can get different default on grub menu everytime at startup. I  think I have to add few if/else to do this. but I am unable to do.  please tell me how can I achieve this?

---

### Post by Krytarik on 2010-11-29
Hi alokmahor,

IMHO it isn't possible to do this inside the grub.cfg itself, but you can use an externel script to change the default-value accordingly. You can achieve this via the "sed"-command (I just googled it):

```
sed 's/default="0"/default="4"/g' /boot/grub/grub.cfg
```

or

```
gksudo "sed 's/default="0"/default="4"/g' /boot/grub/grub.cfg"
```

depending on the way you decide to invoke the command (via "crontab" you don't have to use "gksudo").

I hope it helps.

---

