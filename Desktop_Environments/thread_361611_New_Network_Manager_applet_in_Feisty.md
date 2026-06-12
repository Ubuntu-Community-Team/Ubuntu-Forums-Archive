---
title: "New Network Manager applet in Feisty"
date: 2007-02-14
forum: Desktop Environments
---

### Post by brettg on 2007-02-14
Hi all

I'm trying out Feisty and have a question regarding the Network Manager applet that is installed on the gnome menubar (up near the volume control tool)

Background. The machine I'm running has a GigE LAN port (ETH0) as well as WiFi (ETH1). 

I'm using the WiFi interface and the LAN port is usually disconnected.

My question is how do you configure this applet thing? It appears that it is currently monitoring ETH0 (which is disconnected) so the icon is shown with a little red cross on it and when you hover over it it says "No Network Connection".

Left clicking does nothing, right-clicking gives three options, an "Enable Networking" checkbox, a GREYED OUT radio button called "Connection Information" and "About" which simply provides a url to this website.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

Un-checking "Enable Networking" does nothing, you can't do anything with the greyed out option and the about is useless. The website it links to has no documentation or help that I can find.

So, my question is how do I change the settings for this applet? How do I tell it to ignore ETH0 and monitor ETH1? I've looked through the new Control Center but can't find what I'm looking for.

Does anybody know anything about this applet?

---

### Post by pebo on 2007-02-14
The documentation
/usr/share/doc/network-manager/README.debian
might help

---

