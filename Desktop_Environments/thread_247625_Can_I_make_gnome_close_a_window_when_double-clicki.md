---
title: "Can I make gnome close a window when double-clicking on the left upper corner ?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by jeepescu on 2006-08-30
I find it annoying to have to move my mouse to the right corner to click on the X to close a window.

Most of the mouse activity takes place in the left upper corner of the desktop, i think it would be nice to be able to close a window from that area too.

Am I asking too much ? 

Thanks in advance, 
BN

---

### Post by mssever on 2006-08-31
I don't know if you can make Metacity work like Windows, but you can move the close button to the left. Type "gconf-editor" and drill down to /apps/metacity/general. Edit the key "button_layout" to your liking. For example, you could set it to ```
menu,minimize,maximize,close:
```

---

### Post by jeepescu on 2006-08-31
mssever, you ROCK !!!!

---

