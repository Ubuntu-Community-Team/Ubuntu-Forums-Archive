---
title: "awn without xgl"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by pacsum on 2008-02-07
Can I install and set AWN to work without having compiz and XGL?

---

### Post by nilarimogard on 2008-02-07
If you have AWN installed, disable compiz, run this in a terminal window:

sudo apt-get install xcompmgr
then this: xcompmgr && avant-window-navigator

Should work...

---

### Post by pacsum on 2008-02-07
When I put the xcompmgr && avant-window-navigator command on the startup programs, Nautilus fails to start.

---

### Post by Tenken on 2008-02-07
Try adding a '&' after AWN to run the programs in the background

```
xcompmgr && avant-window-navigator &
```

---

### Post by pacsum on 2008-02-07
> **Tenken said:**
> Try adding a '&' after AWN to run the programs in the background

```
xcompmgr && avant-window-navigator &
```

It doesn't work either :-k

---

### Post by Tenken on 2008-02-08
Try either putting the command in parentheses

```
(xcompmgr && avant-window-navigator) &
```

or just making a separate entry for each program

```
xcompmgr &
avant-window-navigator &
```

---

