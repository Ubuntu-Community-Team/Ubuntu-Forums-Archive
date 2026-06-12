---
title: "Logout button freeze system (not a power manager problem)"
date: 2008-10-27
forum: Desktop Environments
---

### Post by Maxim-K on 2008-10-27
Hi,

after system freeze logout button stopped working. I've googled and discovered that this is usually a problem with gnome-power-manager which is not loading on startup. I've checked my startup list, but gnome-power-manager was there, and it seems to be running fine. Also if I disable gnome-power-manager in startup list and try to log out from system when gnome-power-manager is not loaded, system freezes about 30 sec later. So it freezes exactly when trying to load logout screen, and gnome-power-manager has nothing to do with it because it's up and running. 

If someone knows what packages are responsible for logout screen GUI and logout operations, please post here and I will try to reinstall them.

Thanks!

---

### Post by goldenfleece on 2009-02-17
I've got a similar problem.
I'm glad you posted because it gives me something to test.

---

### Post by squelchy451 on 2009-02-18
i've got a similar problem but i've went around it by doing this:

copy and paste this into a text manager

#!/bin/bash
gnome-session-save --kill --silent

and save it as logout or something.
Right click and go to properties > permissions. Check the "Allow executing file as program." When u click it, you get logged out!

---

### Post by pschella on 2009-04-02
I am happy to report I have the same problem after an running an update of Ubuntu 8.04.
But strange enough I encountered the problem after a recent update on a OpenSUSE linux machine too.
So it is most likely a bug in the upstream gnome power manager or ACPI in the kernel.
The gnome power manager seems to freeze on both systems and on the SUSE machine when the power off dialog finally appears after 10 minutes or so it no longer has a suspend and hybernate button (which makes me think of ACPI).

---

