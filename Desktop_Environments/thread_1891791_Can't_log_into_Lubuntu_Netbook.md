---
title: "Can't log into Lubuntu Netbook"
date: 2011-12-06
forum: Desktop Environments
---

### Post by Pirate Zoro on 2011-12-06
Whenever I try to log into the lubuntu netbook interface in lubuntu 11.10, lxdm just brings me back to the login screen. How can I log into the netbook version? This is a clean install, my last install worked fine out of the box so I don't know what happened.

---

### Post by phidia on 2011-12-06
Boot in recovery mode, issue > startx report back.

---

### Post by N00b-un-2 on 2011-12-06
either recovery mode or hit ctrl+alt+F1 to get to a TTY.  Then try startx.  If that doesn't work try lxdm (I think it's actually lightdm though...).  If that doesn't work try those commands as root and see what it anything changes.  if root works and your normal login doesn't, you quite possibly hosed permissions in your home directory.

---

### Post by crocodile-mick on 2012-01-23
> **Pirate Zoro said:**
> Whenever I try to log into the lubuntu netbook interface in lubuntu 11.10, lxdm just brings me back to the login screen. How can I log into the netbook version? This is a clean install, my last install worked fine out of the box so I don't know what happened.

The problem is that pcmanfm can't handle a space in the file name. Navigate to the /usr/share/xsessions/ folder and open as root (Tools>Open Current Folder as Root). Right click on the Lubuntu Netbook file and select leafpad to modify the file.  Change the Name=Lubuntu Netbook line to Name=Lubuntu-Netbook or Name=LubuntuNetbook. (You have to eliminate the space between Lubuntu and Netbook). Save the file and exit. Now when you try to login to the netbook session you will notice that it is listed as Lubuntu-Netbook or LubuntuNetbook depending on how you renamed it. Select and Login and you are off to the races.

---

