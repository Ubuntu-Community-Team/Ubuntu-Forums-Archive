---
title: "Ctrl+alt+backspace doesn't restart x server also if hal rule added"
date: 2011-01-25
forum: Desktop Environments
---

### Post by magowiz82 on 2011-01-25
Hi,
since I would like to enable ctrl+alt+backspace to reset x server system-wide I added an this hal rule:
```
cat /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi 
<merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>

```

But it doesn't work , ctrl+alt+backspace has no effect

---

### Post by magowiz82 on 2011-01-25
I think I solved : I used gnome-keyboard-properties and clicked apply globally, then I enabled ctrl+alt+backspace to restart X

---

### Post by margarettefox on 2011-01-25
> **magowiz82 said:**
> I think I solved : I used gnome-keyboard-properties and clicked apply globally, then I enabled ctrl+alt+backspace to restart X


Does it really works?

_____________
  [lab   coats for sale]("http://www.justlabcoats.com/")

---

### Post by magowiz82 on 2011-01-25
yes it works

---

