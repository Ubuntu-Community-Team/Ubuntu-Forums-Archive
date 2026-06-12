---
title: "apt and ftp failures related to modem"
date: 2006-06-26
forum: Desktop Environments
---

### Post by m_pav on 2006-06-26
I have been researching this issue for a few weeks now, because my system has had troubles on and off for some time now, the best part of this year and I need to get to the bottom of it.

It appears to be all related to hardware, not software, though there could be some issues with drivers in some setups. Routers and LAN cards with DHCP are failing all over the place but only when using apt of ftp, all other internet connectivity has full functionality. How can I be so sure? I have a laptop and I do some house or place of business calls fixing up peoples problems (those poor people, they all run windows and 90% of them have viruses - shame they chose the lesser, because I always show them Linux). Many of them have broadband, so I can just plug in to their modems and with their permission, test apt and ftp, so I have in a sense, access to a broad variety of testing stations.

My laptop will not connect to apt while I am at home or work unless I change the dns server in my network settings to use a dns server outside of my LAN, instead of the modems built in dns server (identical modems) but apt almost never fails when I connect to a different brand or model of modem, so I believe it's related to hardware, not the sources.list or /etc/network/interfaces. I can remove my expensive modem and stick in a cheap modem and apt works, same broadband account, default settings all round. I have spent hours trying so many settings including disabling all firewalls in both my laptop and my modem, resetting everything to default many times in the process but still apt would not connect, but put in an el-cheapo modem and it works.

If you are having this problem, contact your modem manufacturer and ask them to fix it with a firmware upgrade. In the meantime, change your settings to use an external dns server like 4.2.2.1 & 4.2.2.2 each time you want to run apt of ftp, but be aware that as your modems lease times out, the dns server will be reset to whatever it was in the first place. Your download will stop, so re-open your network configuration screen, re-type the dns servers and apply the changes, then continue with the download.

[http://ubuntuforums.org/showthread.php?t=193178&highlight=apt+connect+router](http://ubuntuforums.org/showthread.php?t=193178&highlight=apt+connect+router)

Mike P

---

