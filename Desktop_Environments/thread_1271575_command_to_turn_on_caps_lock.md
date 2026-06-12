---
title: "command to turn on caps lock?"
date: 2009-09-21
forum: Desktop Environments
---

### Post by majikins on 2009-09-21
Hi

I would like to know if there is a way to switch on/off caps lock via command line? When an application launches via a launcher button, I want Caps Lock to be on at the beginning of the launch.

Thank you.

---

### Post by ~sHyLoCk~ on 2009-09-21
I only know by xmodmap so install it
```
xmodmap -e "add lock = Caps_Lock"
```

You can alias it in bashrc

EDIT: I don't think that's what you are looking for, after reading your post again.my bad! :)

---

### Post by majikins on 2009-09-21
Yes I've googled that but its not what I require.  I want to be able change on the fly.

Thanks for the response anyway.

---

### Post by majikins on 2009-10-11
bump?

---

