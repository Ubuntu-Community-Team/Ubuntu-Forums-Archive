---
title: "How to change the system name from dell-desktop"
date: 2008-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kezdetj on 2008-10-21
I recently bought an M1530 with Ubuntu 8.04.  It's a great machine, and I like Ubuntu's issue of Linux.  What I haven't found,  and I'm not exactly a newbie (5 years using various distros), is how to change the system, name.  In most distros, you just edit /etc/hostname, but that breaks sudo under Dell's implementation of Ubuntu.  Has anyone else hit this problem?  I definitely do *not* like a system name of "dell-desktop"

---

### Post by ghost_ryder35 on 2008-10-21
what error does it through when you set it?

---

### Post by gbrainin on 2008-10-21
Have you tried resetting it through the network settings?

System->Administration->Network, General tab.

---

### Post by kezdetj on 2008-10-21
Thank you gbrainin!  That was exactly the fix I needed.  I'm still so used to the Debian way of doing things I didn't even think to look for that tool.  But that's what's so cool about Linux: the various forums and community support.  :)  My system name is now Poledra, without breaking sudo.

---

### Post by ghost_ryder35 on 2008-10-21
> **kezdetj said:**
> Thank you gbrainin!  That was exactly the fix I needed.  I'm still so used to the Debian way of doing things I didn't even think to look for that tool.  But that's what's so cool about Linux: the various forums and community support.  :)  My system name is now Poledra, without breaking sudo.
i'm still interested in the error that you got while trying to change it via /etc/hostname

---

### Post by lswb on 2008-10-21
The name must be changed in both /etc/hostname and /etc/hosts. 

Thanks, gbrainin, I didn't know that it could be done through the gui network settings dialog.

---

### Post by gbrainin on 2008-10-22
You're welcome!  Glad it worked.

---

### Post by kezdetj on 2008-10-22
> **ghost_ryder35 said:**
> i'm still interested in the error that you got while trying to change it via /etc/hostname

Basically, sudo was reporting an unknown host anytime i tried to use it.  In debian, you normally only set the host name in /etc/hostname, so i didn't even think about needing to set it in /etc/hosts as well.  Obviously, even after years of using various flavors of Linux, there's still lots more to learn.  :)

---

