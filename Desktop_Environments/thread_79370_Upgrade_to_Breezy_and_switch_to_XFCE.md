---
title: "Upgrade to Breezy and switch to XFCE"
date: 2005-10-20
forum: Desktop Environments
---

### Post by tom-ubuntu on 2005-10-20
Hi Community

Got a question for you:

I setup a "server" (router, firewall, dhcp, central CD-Burner, fileserver, aso) at my parents house. For user convinience I installed Gnome on it. As this machine does not have too much memory (256mb) I am thinking about switching to XFCE. My parents should be able to handle this aswell as it looks similar. 

Now I am not sure how I should do the switch and the upgrade. As I don't have the time to reinstall and configure everything from scratch, I like to upgrade to breezy and doing the switch to XFCE without a new installation. Upgrade first and the switch? Switch first, upgrade then? Anything else I have to think about?

Sorry, my first dist-upgrade with an deb-based distribution :)

Thanks for any tips!

Cheers Joe

---

### Post by Ampersand on 2005-10-20
It doesn't really make much difference which way round you do it, it's probably easier to update first so that you only have to download one set of XFCE packages. Some people have had problems updating from hoary to breezy instead of doing a fresh install. It might not cause any problems, but be prepared to do a dpkg-reconfigure xserver-xorg.

If you're not going to be using Gnome any more, it might be worth considering doing a server install, then getting the xubuntu-desktop package from the universe repository. Most of my installations have taken less than an hour to be fully configured, but it might take longer depending on your hardware.

---

