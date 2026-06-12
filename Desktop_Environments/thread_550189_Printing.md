---
title: "Printing"
date: 2007-09-13
forum: Desktop Environments
---

### Post by Challengerquay on 2007-09-13
Hi all,

Have just tried to set up printing using my Ubuntu desktop as a print server.

I have also added Kubuntu desktop and used KDE control to configure Samba, simple setup just a share with two other PC's running XP.

Have modified the cupsd.conf file  with the following line:

<Location/>
Order Deny Allow
Deny From All
Allow From 127.0.0.1
Allow From 127.0.0.2
Allow From @LOCAL
Allow From 192.168.1.*
</Location>

To give me the correct IP range on my little network.

I can see the Printer icon on both the XP machines, but not the share, as it will not give me the printer.

The printer is connected to the Ubuntu PC via USB and is printing OK

Help

:confused:

---

### Post by linuxwizard on 2007-09-13
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Challengerquay on 2007-09-14
Sorry Linuxwizard, non of the howto's in the link seem to work.

I have restored the Cupsd.conf file to its original settings and tried to initiate the system as described for Ubuntu 7.04, which is the distro I have got, does not do what it says on the tin, the windows machines will not load the printer.

Could it be that loading Kubuntu desktop is causing the problem? As I am working from the k control panel to set up samba, which I have done for file sharing, but will it give issues with also having GNOME setting up the printer share?

How do I set a printer share up with K control in Samba?

:confused:

---

