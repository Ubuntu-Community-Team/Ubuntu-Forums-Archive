---
title: "PCI Parallel port issue"
date: 2009-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jadecy on 2009-11-23
Ok I'm 99% to where I need to be but now I'm pulling my hair out. I cannot get my PCI Parallel port to work correctly. 
 
It is a brand new Dell studio pc and have loaded Ubuntu 8.04 LTS + EMC2 (machine cnc control). It is dual boot and both OS's run well. The only remaining issue I have is the parallel port. I had to add a PCI card because the motherboard does not have a built in parallel port. 
 
It shows up as: 
 
**lspci**
 
...
04:00.0 Communication controller: NetMos Technology PCI 9815 Multi-I/O Controller (Rev 01)
...
 
 
**lsmod | grep lp**
lp                10636     0
parport        33224     2  ppdev, lp
 
**lsmod | grep ppdev**
ppdev          8580       0
parport        33224      2  ppdev, lp
 
**lpinfo -v**
network socket
network beh
direct hal
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb
 
 
I have searched for a solution everywhere I can think of and tried numerous suggestions but I'm not making any progress. My inexperience with Linux is not helping matters. Please, if anyone has any ideas or debug options it would be greatly appreciated.
 
](*,)  My head is getting REALLY sore!

---

