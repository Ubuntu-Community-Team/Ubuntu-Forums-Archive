---
title: "mythtv 0.20 dapper - floating point exception"
date: 2006-09-21
forum: Desktop Environments
---

### Post by mjziegle on 2006-09-21
I've tried both the official 0.20 release and the SVN and I get a floating point exception when trying to run mythtv-setup or mythfrontend on my local mythbox.

Strangely when I run mythtv-setup or mythfrontend on my laptop over  SSH with X forwarding they work just fine.

Does anyone know where I should start looking to resolve this problem?

---

### Post by tuxinvader on 2006-09-22
You need to have your openGL set up properly before you can use 0.20, because it uses OpenGL to render the GUI. 

If you have an ATI card you will need to install fglrx drivers and X-server module and set our xorg.conf to use it.

If you're on nvidia you'll have to install the nvidia kernel module and update your xorg.conf to use the nvidia driver.

Where did you get your 0.20 packages?

---

