---
title: "Printing with CUPS"
date: 2005-11-16
forum: Desktop Environments
---

### Post by duminas on 2005-11-16
First and foremost, do I need the CUPS server, **cupsys**, installed to print to a Windows machine available behind my router (192.168.x.x), or will the CUPS client, **cupsys-client**, suffice? For reference, right now the client is installed, but not the server.

Secondly, how do I install and make CUPS print to a printer on the other machine? I do not have graphical utilities to do this, and would like to avoid them if possible (so I know how to do it without them, if need be). I would accept using them, but again, if at all possible, I'd like to not do so.

The printer I am trying to print to is a **Canon i560**, which is already shared as Cprinter. I am sure there is documentation somewhere, but I'm just having a lot of trouble finding it.

Aside from this, Ubuntu's behaving fine.
Thanks.

---

### Post by mxyzptlk on 2005-11-16
i suggest you install cups and configure the cupsd.conf file according to your necesities.

cups has a GUI based in http (just type [http://localhost:631](http://localhost:631) after installation) and it willbe easy for you to install any printer even if its in a XP box.

besides theres lots of info in the net related to CUPS, the web interface provides you the user manual and you have access to CUPS.org in order to download the latest CUPS version file.

hope it helps

---

### Post by duminas on 2005-11-17
Bah.
It wants me to open my root account to logins? Forget that; root's off for a reason, and I find the fact that it requires the ROOT USER to be enabled to be flabberghasting. I disabled the check, but this is NOT something I want to do on a production box just to be able to administer printing!

This, and the web interface doesn't understand what my printer is, so I need the command line to install a driver or do whatever it is that CUPS needs so it'll recognize the device.

Any idea?

---

