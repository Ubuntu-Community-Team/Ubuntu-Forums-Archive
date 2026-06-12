---
title: "network card can't be enabled."
date: 2005-09-27
forum: Desktop Environments
---

### Post by satrich on 2005-09-27
I am trying to set-up a home network, and want to use the linux box as internet server.
I use a speedtouch usb modem for the Internet connection. That's all working now. But when I try to connect to other pc's or even when I try to install firestarter as firewall, I cannot connect trough my network card. It is disabled.
When I try to enable it in the configuration centre, then it goes on for a few seconds, and then it disables itself again.
I am suspecting the speedtouch connection to be part of the problem, but I am not sure.

Is there somebody, who can help me here? :confused:

---

### Post by nemin on 2005-09-27
[QUOTE=satrich]But when I try to connect to other pc's or even when I try to install firestarter as firewall, I cannot connect trough my network card. It is disabled.
When I try to enable it in the configuration centre, then it goes on for a few seconds, and then it disables itself again.[/QUOTE]
Reading this, I believe there'll be entry written to /var/log/messages about this. Have a look this file.

---

### Post by satrich on 2005-09-28
OK. I have my network card enabled now. I don't really know what caused the problem, but it is working now for that part.

Now the next problem:
I can not start firestarter. I tried to remove it with apt-get remove firestarter, ande reinstalled with apt-get install firestarter but this is what I get:
*****************************************************
Preconfiguring packages ...
Selecteren van voorheen niet geselecteerd pakket firestarter.
(Database inlezen ... 62706 bestanden en mappen ge&#239;nstalleerd.)
Uitpakken van firestarter (uit .../firestarter_1.0.1-1ubuntu2_i386.deb) ...
Instellen van firestarter (1.0.1-1ubuntu2) ...
Starting the Firestarter firewall: failed.
invoke-rc.d: initscript firestarter, action "start" failed.

So the installation went well, but whenever I try to start firestarter it fails. When I try it as root, the same problem occurs.

It's strange because the other day when my network card was not eneabled, I could start firestarter, but then the firewall couldn't be activated, because of that network card.
And now my network card is detected and enabled, firestarter won't even start up.

Anyone has an answer,?
thnks.

---

