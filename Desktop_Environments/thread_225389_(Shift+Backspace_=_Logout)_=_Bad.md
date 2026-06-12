---
title: "(Shift+Backspace = Logout) = Bad"
date: 2006-07-29
forum: Desktop Environments
---

### Post by sportman1280 on 2006-07-29
How do i disable the shift backspace shortcut.  I lose all my windows and information i have typed way to often with that shortcut and its annoying the crap out of me.  (I lost my post once while trying to post this cuz i hit it mid post....)Any ideas?

---

### Post by cptnapalm on 2006-07-29
Using Xgl?

---

### Post by sportman1280 on 2006-07-29
sure am

---

### Post by chalex on 2006-07-29
```
xmodmap -e "keycode  22 = BackSpace"
```

Searching google for "disable shift backspace" or the command above will give you more info.

---

### Post by sportman1280 on 2006-07-29
Thanks man.

---

### Post by d351GuJu on 2006-07-29
Thanks for that command, saved me some time!  ;) :)

---

