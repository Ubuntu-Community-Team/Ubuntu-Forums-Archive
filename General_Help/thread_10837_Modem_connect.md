---
title: "Modem connect"
date: 2005-01-11
forum: General Help
---

### Post by vlatkop on 2005-01-11
I little fresh in Ubuntu and at first I must say bravo for the team for this beautifull distribution. My question is: I didn't found any program to connect to the Internet via modem. Do I have to install particular program like Kppp or something similar? Thanks

---

### Post by az on 2005-01-11
You may use the netorking utility to connect with a modem, but it is more like a braodband connection utility.  For example, it asks you if you want to connect at boot time - no dialup user really needs that.

There is an applet called modem-lights.  Right-click on your panel and add the applet.  You must set the default commands and the lock file name to your modem device.

You may use pon and poff to connect and disconnect.  Use sudo pppconfig to configure the options.  Go into the advanced options menu and add your user to the dip group so that you have the permissions to dial and hangup.  You must log out and back in to update your permissions.

Your modem device is (for a serial modem) /dev/ttyS0 for your first serial port (com1) /dev/ttyS1, ttyS2 (note the capital S)
/var/lock..ttyS1   (change this name to the appropriate device)

If you have a winmodem, google for scanModem, a utility that will tell you if there are drivers available for your modem.  Many of these software modems can work under linux.  Some only have drivers that cost more than the modem itself...

Good luck!!

---

