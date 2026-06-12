---
title: "No Wireless"
date: 2009-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Yizi on 2009-11-01
Installed Ubuntu 9.10 and it does not pick any wireless up, when i click on the icon it says wired network and VPN connections.

Any idea?

---

### Post by unamanic on 2009-11-01
> **Yizi said:**
> Installed Ubuntu 9.10 and it does not pick any wireless up, when i click on the icon it says wired network and VPN connections.

Any idea?
Did it work on the live CD?

Did wireless work under 9.04?

Does it offer any restricted drivers?

What is the output of lspci?

---

### Post by Yizi on 2009-11-01
Found out:

Connect to the net using wired connection do a hardware search and active the wireless card.

---

### Post by michael37 on 2009-11-02
I ran into a similar problem as well.  Broadcom STA driver requires some packages in universe repositories.    That means one can't enable these drivers from the default CD (which provides only main and restricted repos).  

A workaround is to connect using wired, enable universe repository.  Then, the desired driver shows up in "Hardware Drivers" and can be installed.

This should be filed as a bug.   Against what?

Which wireless driver did you install?

---

### Post by kukutschka on 2009-11-03
how do I enable universe repository? I can not get wireless to work... Turn it on and of and it says "your system encountered a serious kernel problem" " your system might become unstable and might need to be restarted" but the sistem continues to work perfectly... just under wireless networks it says device not ready... 
Can anyone help please?

---

### Post by michael37 on 2009-11-03
> **kukutschka said:**
> how do I enable universe repository? I can not get wireless to work... Turn it on and of and it says "your system encountered a serious kernel problem" " your system might become unstable and might need to be restarted" but the sistem continues to work perfectly... just under wireless networks it says device not ready... 
Can anyone help please?

Read [What are Repositories?]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Once you enabled universe, go to System -> Administration -> Hardware drivers and enable wireless stuff.

---

