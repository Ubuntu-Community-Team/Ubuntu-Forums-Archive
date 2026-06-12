---
title: "VNC server and key issue"
date: 2010-06-22
forum: Desktop Environments
---

### Post by michellez on 2010-06-22
I have followed the following blog post:
[http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html](http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html)

It works brilliantly except the S and M keys do not type, they active menus on the top bar instead?! S brings up the power button (log off, lock, etc) menu and the M brings up the new mail/social networking menu.

It works fine directly on the machine, it just happens via VNC.

The machine is actually a VM (VirtualBox) on the same machine I am VNCing from at the moment so I'm doing this all from the same physical keyboard, and so I know it's not a stuck key or something.

Thanks
Michelle

---

### Post by michellez on 2010-06-22
FYI, I have VNCed from another machine and the same happens.

I've also tried multiple apps like terminal, gedit, etc and they all do it.

---

### Post by michellez on 2010-06-23
Has any one got *any* ideas please? I need to get this sorted so I can show the system works for implementation.

Thanks
Michelle

---

### Post by Noobile on 2010-09-30
I have the same problem, just chiming in that the host I'm vnc'ing to is not a VM.  Also, I'll note that ordinarily Windows-S and Windows-M do activate these special functions, so maybe VNC is acting like the that key is permanently held down.  I have read about issues with "sticky keys" and VNC, though as far as I can tell  sticky-keys  is not enabled on the host I'm connecting to.

---

### Post by michellez on 2010-10-01
Sorry could have sworn I replied to this at the time. Oops!

It just started working all of a sudden. I suspect a restart somewhere sorted something.

Thanks
Shell

---

