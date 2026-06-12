---
title: "My hicolor theme is broken. Help please!"
date: 2009-07-13
forum: Desktop Environments
---

### Post by Fzang on 2009-07-13
My hicolor theme seems to be broken somehow, meaning the system can't access hicolor. Every other icon theme works fine but if it accesses hicolor for things like app icons and control panel icons it's missing icons.

If I try to update the icon cache with
```
joh@Johs-Zepto:~$ gtk-update-icon-cache -q -t -f usr/share/icons/hicolor
```
I get
```

gtk-update-icon-cache: Failed to open file usr/share/icons/hicolor/.icon-theme.cache : No such file or directory
```

I've already installed hicolor multiple times from synaptic but it doesn't fix it.

So what can I do? Reinstalling would be a pain :/

---

### Post by wojox on 2009-07-13
Did you sudo?

---

### Post by Fzang on 2009-07-13
Yes. Sudo gives the same message.

---

### Post by wojox on 2009-07-13
Try this:

```
sudo gtk-update-icon-cache -f -t /usr/local/share/icons/hicolor
```

---

### Post by Fzang on 2009-07-13
That gives me
```
gtk-update-icon-cache: Cache file created successfully.
```

But the other command still says "No such file or directory".

I tried relogging but it still doesn't work.

---

### Post by wojox on 2009-07-13
Have you looked in usr/share/icons/hicolor and seen .icon-theme.cache?

---

### Post by Fzang on 2009-07-13
There wasn't one. I tried taking the .icon-theme.cache from another set, and then update, but it still wouldn't work.

---

### Post by Fzang on 2009-07-14
Bumpin'

---

