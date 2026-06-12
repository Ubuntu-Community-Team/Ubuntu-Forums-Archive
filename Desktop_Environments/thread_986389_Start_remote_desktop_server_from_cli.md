---
title: "Start remote desktop server from cli ?"
date: 2008-11-18
forum: Desktop Environments
---

### Post by bitrod on 2008-11-18
Hello,

Is it possible to make an ssh connection to my machine logging in as the same user as the desktop user, and from the cli enabling & starting the remote desktop server (allowing to control the desktop without confirmation) ?

So I the can connect to the machine with vnc and control my desktop.

Thanks in advance.

---

### Post by johnkzin on 2008-11-18
I think you can do something like that with x11vnc, if you know the display and all of that.

---

### Post by krunge on 2008-11-18
> **bitrod said:**
> 
Is it possible to make an ssh connection to my machine logging in as the same user as the desktop user, and from the cli enabling & starting the remote desktop server (allowing to control the desktop without confirmation) ?

So I the can connect to the machine with vnc and control my desktop.

Yes, you can do that with x11vnc:

[http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)

---

