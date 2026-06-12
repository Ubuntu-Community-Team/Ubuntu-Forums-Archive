---
title: "[SOLVED] Help with xwinwrap"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by CowzRule on 2007-07-30
When I try this command```
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/share/applications/screensavers/Floating Feet -window-id WID
```I get a "Floating" not found error. I believe I need to use quotation marks to to enclose the command but I'm not sure where I put them. Thanks

---

### Post by jpkotta on 2007-07-31
I will assume that "/usr/share/applications/screensavers/Floating Feet" is a poorly named file you want to pass as an argument, and not a file called "/usr/share/applications/screensavers/Floating" along with a "Feet" argument.  Space delimits arguments by default, quotes will effectively make spaces literal, and cancel their  delimiter property.

```
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- "/usr/share/applications/screensavers/Floating Feet" -window-id WID

```

[http://www.gnu.org/software/bash/manual/bashref.html#SEC8](http://www.gnu.org/software/bash/manual/bashref.html#SEC8)

---

