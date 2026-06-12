---
title: "Problem in enabling visual effects"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by alamjadtawfiq on 2008-01-26
Hi there,

I am trying to enable the visual effects, but when I try to do so, I always receive a message that says:
"The Composite Extension is not available".

I went to synpatec, and searched for 'Composite Extension', and downloaded 
libxcb-composite0
libxcb-composite1 (already installed)
xproto-composite-dev

but the same message appears, what should I do?

---

### Post by hhhhhx on 2008-01-26
try re-install the driver through envy

---

### Post by alamjadtawfiq on 2008-01-26
The driver of what?

---

### Post by runemaste644 on 2008-01-26
I would recommend using restricted drivers manager instead. Envy is unsupported.

---

### Post by alamjadtawfiq on 2008-01-26
I reinstalled it.. but the same message appeared. What might the problem be?

---

### Post by Ub1476 on 2008-01-26
You need to install XGL. You can uninstall those other packages you installed (except for the video driver of course).

```
sudo apt-get install xserver-xgl
```

Remember to re-login

---

