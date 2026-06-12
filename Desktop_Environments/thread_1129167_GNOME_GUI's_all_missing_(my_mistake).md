---
title: "GNOME GUI's all missing (my mistake)"
date: 2009-04-18
forum: Desktop Environments
---

### Post by flyingsliverfin on 2009-04-18
I was trying to make the boot run faster, so I went to the services window.

there I unchecked all the things that I didn't need.

when I reached the place where it said "graphical login(gdm)" I unchecked it, thinking it was only the login window that would be TTY. However, now everything is text-based. how do I get GNOME up and running again from the TTY1? ty

---

### Post by justsomedude on 2009-04-18
1. Login on the text console.

2. ```
sudo /etc/init.d/gdm start
```

3. Reenable graphical login.

---

### Post by flyingsliverfin on 2009-04-18
thx

---

