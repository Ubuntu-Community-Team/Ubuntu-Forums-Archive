---
title: "Vostro 1400 Nic to 1Gbit??"
date: 2009-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dfrandin on 2009-07-02
I have a Vostro 1400 with 8.04 installed.. Works fine but for one pesky thing.. I use the laptop 95% via wifi, and the few times I've connected to the onboard nic, its been on a 100mb switch, but now I have the need to move a lot of Virtualbox virtual machine disk images around between another machine with a Broadcomm 5700 nic and this laptop.. The other machine is running Vista, and to help these vm moves, I bought an 8-port 1000/100/10 switch. The port connected to the other machine shows a gigabit link, but the Vostro only shows a 100mb link.. Since both machines have the same Broadcom NeteXtreme adapter, is there a magic incantation I need to do on the Linux side to get a gigabit link??

Further checking:
ethtool says that the adapter only supports 10/100baseT full/halfduplex..
lspci says:
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (Rev 02)

Also the other end of my "link", a Dell GX620, which is running Vista, but has a Broadcom 57XX network adapter does gigabit fine...

Apparently this newer 59XX version of the adapter DOESN'T... What IS the magic incantation to get this $@@@#% Broadcom POS to do what its mfgr SAYS its supposed to do.. Apparently this is NOT just Linux, as I put my Vista and Win7 disks into the laptop, and they do not run the adapter at gigabit EITHER... 



Dave

---

