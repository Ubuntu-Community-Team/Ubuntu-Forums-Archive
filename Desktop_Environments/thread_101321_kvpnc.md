---
title: "kvpnc"
date: 2005-12-09
forum: Desktop Environments
---

### Post by jasplund on 2005-12-09
I'm trying to connect to the VPN server at my work

I have host name vpn.umb.no and username and password

I'm using kvpnc and get this message:
"debug: Trying to connect to server " 128.39.175.2" with user "johaas"... 
info: "pppd" started.
error: [pppd err] /usr/sbin/pppd: invalid parameter 'nodeflate' for bsdcomp option "


How do I fix this?
btw I'm using guarddog as firewall.

---

### Post by steevc on 2006-02-01
I had something similar. Try setting Do not use BSD compression in the PPTP settings.

Are you using kvpnc 0.8? There are new versions available that may fix some of the stability issues. I did manage to get it to connect to my office, but have not worked out how to route addresses on the work network. Then it started losing all my settings. This version is very unstable.

I tried to instal 0.8.2.1 from source. I had to install autoconf and automake, but still get some errors about a lack of KDE headers. I don't know what I need to install.

---

### Post by elamericano on 2006-05-16
kvpnc worked for my pptp connection too, with No BSD and No EAP, and just like you, I couldn't get the route to be added. I can type it into the profile, but it won't save it. Ridiculous. I tried to work around by running an "after connect" command to add a route to ppp0. On the first try it decided to use ppp1. @#$% ](*,) 

I'll have to run a script to get my routes always correct, but when I add it manually, it works. I see there are deb packages for 8.2.1 now, but the dependencies aren't in the repositories. It looks like it won't be possible in Breezy. Oh well, I needed 8.3 or 8.4 for the bug fix anyway.

---

