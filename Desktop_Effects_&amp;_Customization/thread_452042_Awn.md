---
title: "Awn"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by stickperson on 2007-05-22
Do you have to be running a XGL session to install and use awn?  What exactly is an XGL session anyway.. what makes it different from the deafult?

---

### Post by xenoph0be on 2007-05-22
You have to be running a compositing window manager such as beryl or compiz for AWN to work correctly.

You can see if your x session supports direct rendering by typing/pasting the following into a console window.

```
glxinfo |grep direct
```

---

