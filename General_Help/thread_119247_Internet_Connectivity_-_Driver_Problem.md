---
title: "Internet Connectivity - Driver Problem?"
date: 2006-01-19
forum: General Help
---

### Post by nutsobilly on 2006-01-19
I recently loaded Ubuntu with GNOME on a old Gateway Intel box...it was a 450 Mhz Pentium 3.  The Ethernet card is a Acction Technologies Corporation EN-1207D Fast Ethernet Adapter.  At times, the internet connectivity hangs and don't get any internet connection from the Linux environment.  Is there possible a driver issue with my Ethernet card (for instance...the auto-update feature of the OS does not work...including when I try and download most anything else from web sites)?  If so, how would I find a resolution?

---

### Post by handy on 2006-01-19
Do the following to remove IPv6 from your Ubuntu system, IPv6 can cause your internet connection to be slow, or, as in my case, not work at all!!

Type about:config no quotes into the location bar in Firefox (this may work in Opera?)

Then type ipv6 into the Filter field.

Double left click on the line that comes up to change it's boolean value to True

sudo gedit /etc/modprobe.d/aliases

Change this line: alias net-pf-10 ipv6

To this: #alias net-pf-10 ipv6

(# = commented out), Save & Exit

Now you can forget about ipv6, possibly for years.

Note: If you have organised to have a Static IP Address with your ISP the following does not apply to you.

Another thing that can slow your internet connection down, is if you have Static IP Address selected instead of DHCP, to check this:-

Goto - Menu: System/Administration/Networking double left click on your ethenet device - usually eth0, this will bring up the Interface Properties dialogue.

Now check that the Connection Settings - Configuration: pull down says DHCP.

DHCP is much faster when changing connections from server to server.

If your setting is Static IP Address, it will take a long time to load a page from a New server. Once on that server the pages should load normally, until a page is called from a different server, then that page will be slow to arrive.

Both of the above are critical for my internet conection & speed, I hope they work for you, they won't hurt atleast...:KS

---

