---
title: "Gutsy Network Manager boot loop on eth2"
date: 2007-06-22
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-06-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/121652](https://bugs.launchpad.net/ubuntu/+bug/121652) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In daily-live 20070621, CD Live /var/log/syslog is chock full of hundreds of entries as follows.  I don't have an eth2 that I'm aware of, but Network Manager is convinced there is one and almost never lets go.  It's an IBM NetVista A30p 2 GHz P4 other details in bug report

Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) started... 
Jun 22 14:56:33 ubuntu NetworkManager: <WARNING>^I nm_dhcp_manager_begin_transaction (): dhcdbd not running! 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) failure scheduled... 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) failed. 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IDeactivating device eth2. 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth2'. 
Jun 22 14:56:33 ubuntu NetworkManager: <WARNING>^I nm_dhcp_manager_get_state_for_device (): dhcdbd not running! 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IWill activate connection 'eth2'. 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IDevice eth2 activation scheduled... 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) started... 
Jun 22 14:56:33 ubuntu NetworkManager: <information>^IActivation (eth2) Stage 1 of 5
---- these sets of messages loop on and on and on ......

Cheers, Jerry:(

---

### Post by Erik Andrén on 2007-06-23
Yeah, I have the same issue right now.

---

### Post by jerrylamos on 2007-06-24
Today's level 20070624 has same eth2 loop problem.  /var/log/syslog is 3,616,189 bytes that's well over 3 megabytes almost all the Network Manager eth2 loop.  

Sure wish the Network Manager was optional since as delivered it comes with bugs like this one where it totally forgets it just tried eth2 and it won't work must be thousands of times.  

Another computer has the Network Manager bug where during boot it disables the Realtek ethernet adapter which is the only network connection, requiring manual clicking to get Network Manager to try again at which point it works fine.  That's been a Network Manager software bug on Feisty as well.

Cheers, Jerry:(

---

### Post by jerrylamos on 2007-06-26
June 26 build 20070626 slower yet in booting up.  On another motherboard built computer, syslog is 35,000 bytes.  Today, on IBM NetVista A30p Pentium 4, syslog is 5,189,000 bytes chock full of the Network Manager loop, this time on eth0 which I do have and am using now.

Sure does slow down boot.

I'll give a go on the Thursday build to see if it is any better.

Cheers, Jerry:(

---

