---
title: "Lose desktop effects after logout and login again"
date: 2009-04-06
forum: Desktop Environments
---

### Post by syncmasterpt on 2009-04-06
I'm running Kubuntu 8.10 64 bit with an ATI 4870 graphics board and the latest 9.3 64bit display drivers. So far so good.

After a fresh start or a reboot, I logon into my KDE 4.2.2 desktop and I have desktop effects. Running the fglrxinfo command outputs: 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8543 Release

Everything looks ok and works ok. 

But if I logout and I login again, I loose all the desktop effects. It looks like Kwin as connected to the wrong display.

In this case fglrxinfo outputs an error:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17

If I do a CTRL-ALT-Backspace to restart X, the desktop effects start to work again, and fglrxi outputs the initial information.


Any ideas?

---

