---
title: "VNC Auto-allow Connection"
date: 2010-12-06
forum: Desktop Environments
---

### Post by DeadlyAura on 2010-12-06
Right now, I have a few computers set up in my room, but only 2 monitors. Therefore, I typically connect via VNC to use these computers, which works great on my local network.

My problem is that, after Ubuntu restarts, it requires the password for the login keyring before it will allow a VNC connection request. EVENTHOUGH I have it set up to automatically accept incoming connections.

Therefore, before I can VNC to any of these machines after a reboot, (for software updates, etc.) I have to connect a monitor, keyboard, and mouse, just to type in my password.

Anyone know a workaround for this?

---

### Post by DeadlyAura on 2010-12-07
Bump.

Anyone?

---

### Post by asmoore82 on 2010-12-07
You can permanently unlock your keyring.

I wouldn't hesitate to do this at my convenience - is does *not* render your system insecure. It just lowers your security "mode" from password protected to filesystem protected. In other words, only let people you trust access your filesystem. (Duh :P)

To proceed, open "Applications -> Accessories -> Passwords ..."
Right-click your Login keyring, and "Change Password."
Enter your current password and leave both new passwords blank.

This only unlocks your keyring, it does *not* allow you to *login* to your computer without a password. In your scenario, it is GDM's root privileges that login your account on your behalf. From an Internet point of view, the combination of GDM auto-login and an open keyring do not break the security of your system. But, throwing in VNC does. Use your Router's Firewall wisely.

The "Headless" HowTo in my signature does not require opening your keyring, but at the cost of not being able to see the session on a physical montor (VNC only).

---

### Post by DeadlyAura on 2010-12-11
I tried this... but it is still requiring me to enter in my keyring password before it will allow a VNC connection...

---

### Post by DeadlyAura on 2010-12-15
Bump

---

### Post by dddw on 2010-12-17
try this
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

