---
title: "compizconfig-settings-manager and keeping more than 1 window above"
date: 2009-08-03
forum: Desktop Environments
---

### Post by v1nsai on 2009-08-03
I'm using cairo-dock as my top dock and awn as my taskbar, so I want both of them to stay above all other windows and the gnome panel (yes I'm still using that too) but when I tried just clicking the '+' next to 'Above' in Window Rules, it adds Awn so the line looks like this

```
(class=Cairo-dock) & class=Awn
```

This actually makes neither of them work.  By removing the paranthesis from cairo dock I was able to make that one work again, but I still can't figure out how to add Awn.  Could anyone show me how I would write this?  I've tried all sorts of different combos of &'s and commas and semicolons but nothing has worked I figure someone has probably already had and solved this problem before anyway

---

### Post by v1nsai on 2009-08-06
Bumping, still haven't figured it out.  I think I'm going to submit a bug report too, the program tries to add other classes but it breaks the whole line when it does.

---

### Post by v1nsai on 2009-08-07
Well, submitted a _[bug report](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/410438)_ but I have to wonder if I'm the only one getting this and if maybe there's just something wrong on my end.  This is still a pretty new install so I don't know what to call it.

---

### Post by Sanemind on 2009-08-22
You need to change the & to | 

(class=Cairo-dock) & class=AwnOnly 

would match a window that has both class Cairo-dock AND class Awn, which is clearly impossible! It's like saying if X=1 and X=2 at the same time, a logical impossibility. I mean, this is second grade logic ;)

You want to use the OR operator, not the AND operator, which is the vertical bar. '|', not the ampersand '&'. 

So change it to:
class=Cairo-dock | class=Awn

and you'll be fine.

---

### Post by v1nsai on 2009-08-23
I see what you're saying, that makes sense.  I was thinking of it in terms of a command instead of a regex, good call thanks a bunch for responding.

---

