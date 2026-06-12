---
title: "gdm and xdmcp"
date: 2007-12-01
forum: Desktop Environments
---

### Post by dcherryholmes on 2007-12-01
All the howto's I've read describe enabling xdmcp in the security tab of the gdm configuration GUI.  It doesn't appear in any of my Gutsy installs.  Is this a bug or am I missing something?  I've tried enabling remote connections first, and I see the configure xdmcp button at the bottom, but there's still no xdmcp option in the security tab.  I also tried editing /etc/gdm/gdm.conf by hand, and removing gdm-custom.conf, to no effect.

---

### Post by scxtt on 2007-12-01
you can enable xdmcp via the "login window" in the default menu ... i just did it 2 days ago in gutsy - i set "remote login" to be "same as local".

---

### Post by bnuytten on 2007-12-16
Also using Gutsy, enabled XDMCP but there was no process listening on udp port 177. Had to reload gdm and restart X to have XDMCP listening on port 177.
[CODE]
sudo /etc/init.d/gdm reload
[CODE]
prompts that the settings will be in effect when all X sessions are closed. If all users log off from their X sessions on the XDMCP server, it should be enough I think but I just pressed ctrl+alt+F1 to restart X. Save your work before you do!

---

