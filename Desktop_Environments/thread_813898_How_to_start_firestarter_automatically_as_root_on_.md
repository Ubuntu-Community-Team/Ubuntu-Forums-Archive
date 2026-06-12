---
title: "How to start firestarter automatically as root on system startup."
date: 2008-05-31
forum: Desktop Environments
---

### Post by priyank_bolia on 2008-05-31
How to start firestarter automatically on system startup. I know using the session method, gksu /usr/sbin/firestarter
but I don't want to enter password each time, how to start it automatically as root.

---

### Post by mike2357 on 2008-05-31
I'm curious:  Why do you want to do this?

---

### Post by priyank_bolia on 2008-05-31
I want to start firestarter automatically on system startup, or say any other program. I just want to know how to start programs automatically with root privilege

---

### Post by Closed_Port on 2008-06-01
You can use your sudoers file to do it. Here's a good howto:
[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

However, running firestarter automatically is not a good idea but a security risk. You don't need to run the firestarter gui for your firewall to work. It will happily work in the background, once you used firestarter to set it up and so there's really no reason to start the gui without a password.

---

