---
title: "Multiple network profiles?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by kikinovak on 2006-08-31
Hi,

I have Ubuntu 6.06 installed on my Fujitsu laptop, which I use at home as well as at work. I'm a sysadmin for a computer room (running mixed Linux / Windows) as well as some public libraries. I recently migrated to Ubuntu after several years of working with Slackware Linux (from 7.1 to 10.2).

Is there a way to have multiple network profiles? I connect to all sorts of networks, managed statically or via a DHCP server, connected either via Wireless or eth0 (unfortunately, my Wifi Ralink driver does not support bridging yet). 

Anyway, until now, first thing I do is edit /etc/network/interfaces and - on static networks - /etc/resolv.conf to get connected to the others. In an ideal world, I would just choose my network profile on boot. 

Any suggestions?

---

### Post by Anthem on 2006-08-31
Are you familiar with Network Manager?  It does just what you're looking for, and it's dead simple to set up.  Search the forums for a howto.

---

### Post by dom on 2006-09-20
interesting,

i'm on xubuntu.

i thought you meant the standard network-admin

but after further looking i see network-manager is a daemon and gnome task manager applet.

i installed xubuntu for speed, a light-weight gui, so i hope activating these services as per [http://ubuntuforums.org/showthread.php?t=239178](http://ubuntuforums.org/showthread.php?t=239178) doesn't slow it down too much.

i to do further testing, but i wouldn't see either of these as complete solutions for the problem mentioned.

For instance, is there a way to set up multiple profiles, which are easily selectable from the desktop/taskbar, and which cover such variations in networking related items such as :
[LIST=1]
* multiple nic interfaces, including wireless, ethernet, etc
* wireless nic variations of WEP or WPA, 
* general nic variations of static config, DHCP, etc
* variations on cache setup
[/LIST]

The latter is something for which I haven't gotten around to checking yet so perhaps somebody here has already looked. 

I'm using Xubuntu and Firefox is the default browser.

My networks will include a 
[LIST=1]
* 2 WPA wireless networks, dhcp, no cache
* WEP wireless network, static ip, no cache
* WEP wireless network, dhcp, cache for http, smtp, https, ftp, etc etc
* Ethernet network, dhcp, cache for http, smtp, https, etc etc
[/LIST]

In in the cases where caches exist, network access fails where the caches are not used.

If I can get the system to have various cache settings for different profiles, will Firefox be able to pick this up.

I have not got even the various wireless/ethernet setting working with network-admin :)

So now to try the gnome applet thingy.

In the meantime if anybody has any experiences to share with this, and the cache settings, I'd be glad to hear about it :)

---

### Post by dom on 2006-10-10
its not the full solution but i did find a nice extension for firefox that allows me to easily switch the connection settings for firefox.

this is very handy when moving between environments with different cache address or no cache and just a direct connection (or transparent cache).

saves a few clicks etc.

It's called 'ConnSets' and you can get it at [https://addons.mozilla.org/firefox/3452/](https://addons.mozilla.org/firefox/3452/)

---

