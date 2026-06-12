---
title: "What's wrong with the Control Center?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by NateC on 2005-04-04
When I try to enable my wireless network card by going to "Wireless Network" in the control center I see it blanked out, so I press Administrator mode, and when I do that it returns me to the Control Center start page. It does that whenever I try to go into admin mode. Does anyone know what to do?

---

### Post by jshein on 2005-04-04
Install the gnome package for network management, kde tool is broken really badly right now.

*# sudo apt-get install gnome-system-tools*

you can get to the program by going into the System menu, it will be called simply "Networking"

or you can launch the program by typing

*# sudo network-admin*

Have fun

---

### Post by aramazan on 2005-04-05
[QUOTE=NateC]so I press Administrator mode, and when I do that it returns me to the Control Center start page.[/QUOTE]This sounds like the sudo problem in Kubuntu-preview which is corrected in RC. If you're running Preview, please upgrade to RC (better, wait for the release). If you're already running RC, then I have no idea why kcontrol should behave like that.

---

### Post by lao_V on 2005-04-05
If you want to configure your wireless network in KDE then try the KWiFiManager at the moment which is another front-end to the one in kcontrol. It seems networking is seriously bugged in kde at the moment. It doesn't even work on other distros.

I tried installing gnome-network-tools but everytime I start it, it just hangs..Any ideas?

---

### Post by jshein on 2005-04-05
The package you need is gnome-system-tools

I am runing RC and it is still non-functional, either through kwifimanager or in the control center under wireless.

Trying to configure any networking is problematic through the control center. The administrator button will not work at all, taking you back to the intro for control center.

If you run     sudo kcontrol

you are able to configure the network, but it is buggy. Sometimes it gets an ip by dhcp, but no dns information. Sometimes the network will not come up at all. On next reboot often the network will not come up.

After configuring with the gnome network configuration tool, it works every time.

---

### Post by poofyhairguy on 2005-04-05
[QUOTE=NateC] Does anyone know what to do?[/QUOTE]

As someone else said, use Gnome tools. Most major KDE distros (MEPIS, SUSE, MANDRAKE, etc,) have a custom GUI tool for networking because KDE lacks one. Its its biggest problem as a desktop environment. Yet every tool I've tried (except the one that comes with Fedora, even though I think that is GTK program anyway) has a network manager that does not even think about touching Gnome's.

---

