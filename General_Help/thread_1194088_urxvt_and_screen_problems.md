---
title: "urxvt and screen problems"
date: 2009-06-22
forum: General Help
---

### Post by bp1509 on 2009-06-22
d

---

### Post by geirha on 2009-06-22
Try with .Xdefaults instead of .Xresources

As for screen. Do you have a screen-256color under /usr/share/terminfo/ ? I don't, and I'm guessing it defaults to vt100 if you specify a non-existant term.

---

### Post by bp1509 on 2009-06-22
d

---

### Post by geirha on 2009-06-22
I don't know the difference between .Xdefaults and .Xresources really, but if you do an strace on urxvt, you'll see it doesn't try to open .Xresources (at least not on my hardy install)

```
strace urxvt 2>&1 | grep '^open.*\.X'
```

According to the comments in this bug-report: [https://bugs.launchpad.net/ubuntu/+source/screen/+bug/87966](https://bugs.launchpad.net/ubuntu/+source/screen/+bug/87966), the first three lines you have should be enough to get 256 colors in screen, so drop the "term screen-256color"-line and see if that works.

EDIT: I tried it myself, and tested with the colortest script mentioned in that bug report ( [http://www.vim.org/scripts/script.php?script_id=1349](http://www.vim.org/scripts/script.php?script_id=1349) ). Worked for me.

---

