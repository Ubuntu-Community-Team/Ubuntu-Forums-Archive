---
title: "kubuntu and cups: remote printer"
date: 2006-08-11
forum: Desktop Environments
---

### Post by kvtb on 2006-08-11
Hi,

I've a small network with one server (Debian sarge) and two clients (Debian sid and Kubuntu dapper), The server has a USB printer attached to it.

On the Debian client, all I had to do is install cupsys-client, and add a line 

ServerName debianserver

to the file /etc/cups/client.conf

En then everything works, OpenOffice, KDE Printing, etc. This was only a few seconds of work!


The Kubuntu machine however, is driving me crazy. The default cups config is very strange and overkill for what I want. I removed the cupsys (server) package, and added a file /etc/cups/client.conf with a single line ServerName debianserver.
Printing from OpenOffice.org works, lpstat -p shows the printers attached to the server, etc. But... KDE Printing's CUPS module is stubborn and refuses to connect to debianserver:631.

It looks like localhost:631 is hardcoded in KDE printing, since it always defaults to this setting and I have no idea where this is configured.

Does anyone know how I can configure the Kubuntu machine to make it work just like the Debian machine (ie. no need to install the cupsys server package, almost zero configuration, KDE print should connect to debianserver:631)?

Thanks in advance.

---

### Post by kvtb on 2006-08-12
I finally got it working.

I had to edit the file /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdeprintrc

and edit the line host=localhost

save and run kconf_update

and now also the KDE printing system connects to the remote print server.

---

