---
title: "Authorizations:: Shutdown when multiple users logged in"
date: 2009-02-09
forum: Desktop Environments
---

### Post by goehle on 2009-02-09
A new feature of Intrepid is that the average user is not allowed to shutdown the computer when multiple users are logged in.  I've been trying to disable this but am having some trouble.  If you shutdown using the system menu when multiple users are logged in then an authorizations window pops up.  So I tried using the authorizations tool to change the permissions for org.freedesktop.consolekit.system.stop-multiple-users and org.freedesktop.hal.power-management.shutdown-multiple-sessions so that "Active Console"  is "Yes".  

I must not understand what I'm doing though, because this doesn't work.  When multiple users are logged in shutting down just brings you to a switch user screen.  Any suggestions?

P.S.  This is not the same as [https://bugs.launchpad.net/bugs/282403](https://bugs.launchpad.net/bugs/282403), although it is related to it.

---

