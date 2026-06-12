---
title: "Seemingly random changing order of eth0-5 mapping to devices?"
date: 2012-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djtopper on 2012-02-21
I've got a new R710 server with the built in 1gb network device (four jacks) and the additional 10gb card (two addition jacks).  The machine also has an iDRAC card so technically there's also a seventh jack but I don't think that's related here.

Although the following feels random, I suspect it's not.  What happens is, sometimes when I boot the machine sets up the devices as follows:

eth0:  1gb jack #1
eth1:  1gb jack #2
eth2:  1gb jack #3
eth3:  1gb jack #4
eth4:  10gb jack #1
eth5:  10gb jack #1

yet other times it does the following:

eth0:  10gb jack #1
eth1:  1gb jack #1
eth2:  1gb jack #2
eth3:  1gb jack #3
eth4:  1gb jack #4
eth5:  10gb jack #2

still other times one of the devices won't show up at all (using ifconfig).

How can I control this?  It's not good for devices to appear, disappear, and have different eth# assigned as I'm only using the first jack on the primary (1gb) card right now.

IE., it's possible to reboot and lose network connectivity.

Also, I have my /etc/network/interfaces file set up to point to just eth0, which (as it's doing currently) has been switched to eth1 as far as the OS is concerned in terms of mapping the HW jacks to eth# devices.

Thanks.

DT

---

