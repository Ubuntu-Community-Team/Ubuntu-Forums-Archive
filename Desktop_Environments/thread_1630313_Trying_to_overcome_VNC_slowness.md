---
title: "Trying to overcome VNC slowness"
date: 2010-11-25
forum: Desktop Environments
---

### Post by trancephorm on 2010-11-25
I need to access existing desktop session remotely, and while it is possible with default VNC server configuration, but the speed is nothing less than catastrophic, and it's not related to network speed at all.

So I'm trying to use FreeNX server, and while it has VNC option, it says VNC protocol is not supported when trying to connect from NX client from Windows. Anyone managed to get this to work? I'm using Ubuntu 10.04.

---

### Post by asmoore82 on 2010-11-25
I like to use VNC with its special packed 8-bit color format: ```
vncviewer **-bgr233** *<remote-machine>*
```

For best interoperability, you can use the VNC translator of the Xrdp software, see the "Perfect Headless Server" link in my signature.

---

### Post by trancephorm on 2010-11-25
8-bit doesn't help, tried it. Will try to implement your guide if you tell me it is possible to enter existing desktop session.

Thanks!

---

### Post by trancephorm on 2010-11-25
Seems like I've found the solution... Will update thread here if it works... [http://en.opensuse.org/SDB:FreeNX_to_existing_display](http://en.opensuse.org/SDB:FreeNX_to_existing_display)

---

### Post by trancephorm on 2010-11-25
Here's another one... [http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/](http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/)

---

### Post by trancephorm on 2010-11-25
And the last one :) [http://www.nomachine.com/ar/view.php?ar_id=AR11B00098](http://www.nomachine.com/ar/view.php?ar_id=AR11B00098) ...

---

