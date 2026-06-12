---
title: "Dapper Always Freezes After about 20-30 Minutes"
date: 2006-06-28
forum: Desktop Environments
---

### Post by adamzap on 2006-06-28
Ever since I installed Dapper, less than an hour after boot, the machine completely locks up, no warning at all (no slowdowns or resource spikes).

This doesn't happen on Fedora Core 4, Fedora Core 5, Slackware, Suse, Musix...(You get the picture)

It has always happened on dapper. Before I installed fglrx and after. I also removed my unneeded startup scripts, no luck.

Here is my hardware:

P4 2.8 Ghz (Northwood)
ASUS P4P800-Deluxe Mobo
1GB OCZ RAM
ATI Radeon 9500 Pro

Can anyone help me diagnose this? I've been using linux for a while, and I'm stumped.

---

### Post by Maggot on 2006-06-28
Mine did too. I have an ATI 9800 Pro. I think it had to do with the driver but cannot remember....it's on here somewhere.

After I installed the ATI driver all was ok.

---

### Post by adamzap on 2006-06-28
yeah, I did install the ATI Drivers (fglrx)

I confirmed this by the output of fglrxinfo

:(

---

### Post by der_joachim on 2006-06-29
Do you have another OS on your machine and if yes, does it have the same problems? 

A non-linux related question: do you have any cooling problems? My previous computer was an Athlon XP box, which overheated regularly. Adding some fans and replacing the old case with a larger one solved my problems. 

Other question: have you tested your memory, or run any hardware diagnostics tools? 

That's all I can think of at the moment. :confused:

---

### Post by Dubbayoo on 2006-06-29
I had some mysterious lockups with ati driver also; mine were doing idle periods so I disabled the screensaver.

---

