---
title: "Direct Download Problems"
date: 2009-04-13
forum: General Help
---

### Post by moss121 on 2009-04-13
I just installed 8.10 on a Dell Vostro 1500 and there is a problem with the internet connection. 

When I am downloading files (both updates and normal firefox downloads) the download keeps freezing after a few MB's stopping for a minute and then restarting. It happens with both wired and wireless connections and I stay connected to the internet because surfing is not affected. After looking through this forum I thought it was a DNS problem first so I turned off all IPv6 settings and used OpenDNS servers but it didn't help. I also installed wicd as I thought it might have been network-manager but that didn't help either. I have no problems when downloading torrents it is only with direct downloading.

I am running 2 computers off the same router and the windows pc has no problems, and before I upgraded 8.04 was working normally so it must be a setting in Ibex. 

Does anyone have any idea what the problem might be?

---

### Post by askreet on 2009-04-14
I can tell you it's not DNS.  If you've already established a TCP connection to begin the download, domain names are out of the picture.

Are you using static IP addressing or DHCP?  It sounds like it might be an ARP or IP conflict.  If you turn off the other PC, does the issue go away?  Have you power-cycled the router?  What if you connect directly to your cable/dsl modem from the computer in question, is it reliable then?

HTH,
- askreet

---

### Post by moss121 on 2009-04-14
Thanks for the reply. I tried resetting the router and a wired connection directly to the cable box but I still have the same problem. I am using DCHP and I have connected without the other computers still no change. I also use mediatomb, media server and when I turn it on it streams with no problems so it is just when connecting to the internet. I thought it might have been an error when installing Ibex so I reinstalled it and it had no effect.
When I am downloading something and it freezes if I stop the download and start it again it works for a few seconds until it stopos again, as soon as i disconnect and reconnect it works, is there any way it could have been set to only download a certain amount per-source or per-connection. 

Thanks again
Liam

---

