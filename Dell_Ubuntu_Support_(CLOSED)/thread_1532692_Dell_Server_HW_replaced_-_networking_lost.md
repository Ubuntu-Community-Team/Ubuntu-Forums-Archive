---
title: "Dell Server HW replaced - networking lost"
date: 2010-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by richardeng2005 on 2010-07-16
HELP! I'm in a serious pickle...

My Dell PowerEdge R200 server just died. Dell had to replace the motherboard, but now networking doesn't work. I'm running Ubuntu Linux Server 7.04 which is a very old version. I think the kernel driver doesn't support the newer revision of the Broadcom adapter on the motherboard. When I try to restart networking, I get the following error:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: no such device

How do I restore networking? Do I require a kernel update? Which kernel version? How do I get this kernel since I don't have network access (so forget apt-get)?

Is there an easier way to resolve this problem?

Do I have to resort to the worst-case scenario of reinstalling *everything* from scratch -- latest Ubuntu version, LAMP, my server application? Dear God!

I hope I don't regret choosing Ubuntu over Red Hat (which is supported by Dell). ;)

Yes, I'm a Linux newbie...

Thanks.

---

### Post by tgalati4 on 2010-07-16
Page through the dmesg and see if any errors are reported:

```
dmesg | tail
```

Boot into BIOS and make sure that the ethernet card is turned on.

Post the details of the network card.

---

### Post by richardeng2005 on 2010-07-16
The dmesg output contains no network errors. There's a reference to 'NET':

NET: Registered protocol family 10

I am unable to get into the bios because I am accessing the server remotely via 'kvm over ip', which the datacentre set up for me. As this is the weekend, I won't be able to go onsite to get into the bios until Monday.

Is there any other way to get the information? Dell informs me that the adapter, which is on the motherboard, is merely a revision of the previous adapter. I think it is unlikely the adapter is 'turned off' -- that's a pretty basic mistake for a Dell engineer to make.

---

### Post by richardeng2005 on 2010-07-16
Excuse me, my mistake. Apparently, with kvm over ip, I *can* get into the bios. Cool.

So here's what the bios tells me:

Embedded Gb NIC1... Enabled without PXE
Embedded Gb NIC2... Enabled without PXE

Further, in the IRQ section:

NIC1... IRQ 15
NIC2... IRQ 14

No other details about the adapter.

Just as I surmised, the adapter is 'turned on'.

---

### Post by richardeng2005 on 2010-07-17
Further information...

I did a 'dmesg | less' and scanned for any references to networking. I found that eth0 was associated with 'Tigon3'.

Doing a Google search, I found that Tigon3 refers to the Broadcom adapter. So apparently the system is able to recognize the NIC. And Tigon3 is supported in all kernels from 2.6.0 and up.

So why am I getting 'no such device' during network startup?

---

