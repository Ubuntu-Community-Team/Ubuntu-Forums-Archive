---
title: "Remote desktop only working when monitor plugged"
date: 2007-12-08
forum: Desktop Environments
---

### Post by perpen on 2007-12-08
Hi all,
I have a Ubuntu 7.10 PC I want to access from a mac. I have remote desktop set up but only works if I start up the Ubuntu with a monitor plugged. Of course I don't want to have a monitor plugged on that machine (not mouse, not keyboard) and when I turn it on without them VNC client from mac gives this error message:

"failed to connect: connection refused (61)"

Maybe is some error message for not detecting t he monitor that prevents it from loggin in? (I have automatic log in). Despite I cannot connect via VNC in this situation I can access the shared folders via smb without any problems.

Tried with and without password, no joy.

Thanks for your time.

---

### Post by Prospero2006 on 2007-12-08
Ok, you need set your desktop to automatically log in when the machine turns on. 


You need to have an active session logged in for vnc to work

---

### Post by perpen on 2007-12-08
I already have automatic log in activated. When the monitor is plugged I can see this is working correctly. Sorry I didn't mention it.

---

### Post by perpen on 2007-12-11
I have changed to various monitor set ups with no success. Is there a way to tell ubuntu to ignore the monitor?

---

