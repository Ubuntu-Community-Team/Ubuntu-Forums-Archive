---
title: "Desktop bar"
date: 2011-03-08
forum: Desktop Environments
---

### Post by boombadaboom on 2011-03-08
Hey guys. I'm running Ubuntu 10.10 32. I was messing around with my appearance and panels and stuff, and I accidentally deleted the default one on the top. I put it back, but it doesn't have the default menus, or the evolution mail, broadcast and empathy icon (the grouped one). Is there any way to get it back to the default one? I'm new to Ubuntu btw. Thanks in advance :)

---

### Post by howefield on 2011-03-08
Might be easier to restore the panels to default, and then put back your customisations, if you had any.

To reset panels to default...

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

---

### Post by boombadaboom on 2011-03-08
Thanks a lot :)

---

