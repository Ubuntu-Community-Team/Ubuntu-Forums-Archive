---
title: "20070129 feisty desktop amd64: network+ubiquity problems"
date: 2007-01-29
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-29
I think that in feisty desktop-live 20070129 amd64 the network is broken (I am testing in vmware). dhcp works ok, ip and gateway are assigned fine but the vm cannot not ping any host outside it.

I've never seen this bug in previous daily feisty builds, so I don't know what to do and how and if this is worthy submitting as a bug using the standard time consuming test procedure.

'sudo dhclient' that I found in bug reports does not change things. I tried to set a static IP but immediately the network notification icon showed "No network devices found", although in Hardware Information the card is still listed correctly as e1000.

I tried dhclient again and it found the card, assigned an ok ip, but still no connectivity. So I gave up. Perhaps removing the network and readding it with modprobe would help, but this is beyond my linux capabilities (/me is ashamed).

In addition the partitioner still exhibits the same well known bugs and since network is absent, I cannot use the alleged workaround (sudo apt-get install debconf ubiquity).

Tomorrow is another day, and another build :-)

---

