---
title: "x11vncserver gnome on Ubuntu 13.10"
date: 2014-01-31
forum: Desktop Environments
---

### Post by Lou_Kitz on 2014-01-31
I'm trying to get x11vncserver to load at startup so I can restart an Ubuntu server 13.10 from a remote desktop and not have to run back to the server to launch the vnc server again.

There are some good guides for this in previous versions of Ubuntu and using different desktop environments.  I'm running the gnome desktop environment on 13.10 and the folders named in the guides don't exist.  With things moving from init.d to startup with this release are there any good step by step guides out yet?  I'd hate to set it to autologin and run a script from that user.

With 11.x I was able to get my Teamspeak server to run from the login screen after a server restart so I was hoping to pull this off as well.

Thanks,

---

### Post by deadflowr on 2014-01-31
What about this
[http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/](http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/)

---

### Post by Lou_Kitz on 2014-01-31
Thanks for the link.  It's short and does use startup triggers, but gnome-desktop-environment doesn't have the lxdm directory this guide calls out in the script.

I started with the 64bit Ubuntu server install and then installed the gnome-desktop-environment over the top.  I have x11vncserver installed and running perfectly.  I can connect using tightvnc but I have to be logged in to start the server.

---

### Post by deadflowr on 2014-01-31
You shouldn't need lxdm.
Follow step2a.
You would need lxdm if you followed step2b.
You can ingore step2c, all together.

---

### Post by Lou_Kitz on 2014-02-01
Well, the first time I tried it it didn't work.  I went through it again and it's working now.  Thank you very much for the help.

---

