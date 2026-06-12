---
title: "Counter-strike server"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by gabrielpaulsson on 2007-02-08
I have a Intel Core 2 duo E6300, 3GB RAM and a WD Raptor SATA disk with Ubuntu(i386) as my operating system. My problem is that when I host Counter-strike(1.6) servers they run faster then normal, time goes by faster and you run faster. All settings are correct and it must be problem my OS installation. I have made a 2.6.19.1 kernel with 1000hz but that is all. What can be the problem? I have no clue where to look and I have googled alot and just find that Counter-strike clients and dual-core are not a good combination. Is it like this on the server-side too? Please help!

Best regards, 


Gabriel

---

### Post by OscarMedina on 2009-05-06
> **gabrielpaulsson said:**
> I have a Intel Core 2 duo E6300, 3GB RAM and a WD Raptor SATA disk with Ubuntu(i386) as my operating system. My problem is that when I host Counter-strike(1.6) servers they run faster then normal, time goes by faster and you run faster. All settings are correct and it must be problem my OS installation. I have made a 2.6.19.1 kernel with 1000hz but that is all. What can be the problem? I have no clue where to look and I have googled alot and just find that Counter-strike clients and dual-core are not a good combination. Is it like this on the server-side too? Please help!

Best regards, 


Gabriel


I have an      Intel Core2Quad Q9300,      8gb RAM,      750gb SATA and an aditional 160gb SATA HD running      Ubuntu Hardy[8.04] - 64 bit Server Edition, I was also running a Cstrike 1.6 server and also had the faster time issue... 5 realtime seconds where 5.5 ingame seconds and everything was faster too... How I solved this... 
[U]
for 64 bit users:[/U]

```
sudo nano /boot/grub/menu.lst
```and added at the end **no_timer_check**


_in 32 bit OS you can _

```
sudo nano /boot/grub/menu.lst
```and add **clock=pmtmr**  at the end


Then just **reboot** the server and restart your **./hlds** server

---

