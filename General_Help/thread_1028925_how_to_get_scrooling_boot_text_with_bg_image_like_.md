---
title: "how to get scrooling boot text with bg image like in opensuse?"
date: 2009-01-02
forum: General Help
---

### Post by nemp on 2009-01-02
How can I get scrolling boot text messages with background image, like in openSuSe when I press Esc?
Currently I have only scrolling text during boot, but no bg image (I removed 'splash' from menu.lst)

I'm using kubuntu...
btw, sorry about my english x)

---

### Post by Forlong on 2009-01-03
You need to set
```
# defoptions=quiet splash
```
to
```
# defoptions=splash
```
in /boot/grub/menu.lst

And of course **do not** remove the splash option.

---

