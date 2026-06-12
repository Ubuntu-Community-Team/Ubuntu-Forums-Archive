---
title: "Dell D620 - wired ethernet not detected"
date: 2011-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dbrb2 on 2011-01-26
Hello,

I am running Ubuntu 10.10 (and before that 10.04) 

On both of these releases, my wired ethernet interface is not detected, and is not shown on typing lspci into the terminal 
(wireless works  fine) 

I have found that removing the power cord and battery then rebooting sgave me my adapter back once (when still running 10.04) - but only until the next power down. 

I have found a few people referring to the above workaround, but have not yet found a fix. If I can persuade my dell to see my interface again, I will post its details here. 

Can anyone suggest any likely solutions or useful debug tips? 

Cheers,

Ben

---

### Post by dbrb2 on 2011-02-01
Fixed - in the BIOS the NIC was set to "Enabled (with PXE) - default"

I set it to merely "enabled" - and now it is reliably detected by Ubuntu each time the machine boots

---

