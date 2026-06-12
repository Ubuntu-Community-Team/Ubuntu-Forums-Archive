---
title: "Getting the WG111 working in ubuntu"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Dracling on 2005-11-04
I know that this question has been asked many times before, but I've tried everything reccommended in the wiki as well as many forums and nothing works ...

I use the Netgear WG111 Wireless G USB adaptor (version one) to connect to the internet, but I can't get to to work, the specifics are below.

I installed the netwg111 windows drivers off the Netgear CD by using the version of ndiswrapper on the ubuntu installation CD, and that worked fine. When I type "nidswrapper -l" it tells me that both the hardware and and software to present for the netwg111 drivers. But when I type "modprobe ndiswrapper" nothing happens, the light on the device doesn't come on, there's no change. If I type "tail /var/log/syslog" after modprobe, I get a message saying that the windows drivers failed to initialize the device. Because of that, wlan0 is not recognized and I can't set it up.

I've tried multiple versions of ndiswrapper and all the drivers on my CD, I've even reinstalled ubuntu, but I keep getting the same error. Does anyone have any idea about how I can fix this?

---

