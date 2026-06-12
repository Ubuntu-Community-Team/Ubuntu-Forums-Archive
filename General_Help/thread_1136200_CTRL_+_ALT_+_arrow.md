---
title: "CTRL + ALT + arrow"
date: 2009-04-24
forum: General Help
---

### Post by Cacaco on 2009-04-24
Is it possible to turn the display upside down (like windows does) when you press CTRL + ALT + ARROW UP or DOWN?
If not...do you know any program that does that for linux?

Thanks

---

### Post by Kareeser on 2009-04-24
Give this command a try:

```
xrandr --output VGA --rotate inverted
```

Your output may not be called "VGA". Check what it is by running xrandr with no switches.

Edit: Yup, works with my Intel 855GM. Man, that's seriously trippy. Anyway, if you wanted to automate this, you can write some scripts and bind them to a custom keystroke... like ctrl-alt-up and down.

---

### Post by Cacaco on 2009-04-25
Thanks..I'll see how works...

---

