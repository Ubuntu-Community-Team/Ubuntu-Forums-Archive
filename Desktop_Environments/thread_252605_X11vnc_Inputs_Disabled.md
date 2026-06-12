---
title: "X11vnc Inputs Disabled"
date: 2006-09-07
forum: Desktop Environments
---

### Post by paul_manning22 on 2006-09-07
Hi,

I've tried installing X11vnc from ubuntu distribution and also compiling.  It seems when I connect to a session the inputs are disabled.  I can type nothing on the keyboard, and when I click the mouse it does not register.  I can move the mouse on the console no problems but that seems to be the only part that works.  Please help.

---

### Post by krunge on 2006-12-12
Probably missing XTEST library and header file at build time:

[http://www.karlrunge.com/x11vnc/#faq-missing-xtest]("http://www.karlrunge.com/x11vnc/#faq-missing-xtest")

perhaps it is the libxtst-dev package.

---

