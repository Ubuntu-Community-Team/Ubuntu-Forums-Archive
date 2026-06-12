---
title: "Lockdown NetworkManager for one user"
date: 2010-03-02
forum: Desktop Environments
---

### Post by WoPr on 2010-03-02
Hi all!

I have been working on a lockdown proyect, and I need to do the following. Firstly Create a "config" user to get access to printers configuration an network configuration (via NetworkManager) I have locked down everything on this user and works fine. The problems come when the computer is configured, because I need to start session with another user who can't change the network settings, but I fail on this because the nm-applet run with root privileges...

Is anybody knows how to disable mouse over the applet, or lock down it on the user session?

Thanks in advance,
WoPR

PD: I have tried with apparmor, but it does not work (or I don't know how to use it) and I have touched the /etc/dbus-1/system.d/NetworkManager.conf with no luck at all.

---

