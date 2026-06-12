---
title: "My Ubuntu 8.10 keeps freezing"
date: 2008-12-11
forum: General Help
---

### Post by DiGiTY on 2008-12-11
I just did a fresh install of Ubuntu 8.10 (desktop edition) and for some reason it keeps freezing forcing me to power off then back on (then it eventually freezes again!). I can't figure it out to save my life.

I thought it was the vid card (because the same card boggled my old Ubuntu 7.10 installation) so I removed it, but that didn't solve anything. I then thought it was over heating due to lack of air flow or something so I placed it away from the corner to an open floor and it still freezes. I've been running Ubuntu since 6.06 and never ever had this problem before, it's weird.

Any ideas why it keeps freezing and how to resolve it?

P.S. - P4 3.06 GHz, 1 GB RAM, 80 GB HD, DVD-/+RW DL burner, floppy: P4B533-E mobo, old Nvidia AGP vid card, Adaptec RAID card, USB 2.0 PCI card, Trendnet TEG-PCITXR gigabit NIC PCI card, modem (in that order in the expansion slots... maybe move the PCI cards around?)

---

### Post by Titan8990 on 2008-12-11
Post the output for the following:


dmesg

cat /var/log/syslog

cat /var/log/syslog.0

---

### Post by DiGiTY on 2008-12-11
Could not copy & paste or attached code to post, but here's a link to them on the web (I know it's extra work to help someone out for free, but I would really appreciate any effort and help given):

dmesg ouput: [http://rapidshare.com/files/172558784/dmesg-digity-20081211.txt.html](http://rapidshare.com/files/172558784/dmesg-digity-20081211.txt.html)

cat /var/log/syslog output: [http://rapidshare.com/files/172558785/syslog-digity-20081211.txt.html](http://rapidshare.com/files/172558785/syslog-digity-20081211.txt.html)

cat /var/log/syslog.0 output: [http://rapidshare.com/files/172558786/syslog.0-digity-20081211.txt.html](http://rapidshare.com/files/172558786/syslog.0-digity-20081211.txt.html)

It appears the last Ubuntu freeze was at 11:37 PM last night (Dec. 10)

Any ideas?

---

### Post by DiGiTY on 2008-12-13
Anything? Anyone?

---

### Post by DiGiTY on 2008-12-24
moving the PCI cards around and even removing non-crucial cards (USB 2.0 and modem) doesn't help, it still freezes.

Any other ideas?

---

### Post by Titan8990 on 2008-12-24
Sorry, I had missed this post. Put the logs in code tags on the board or use [pastebin](http://pastebin.com/).

---

### Post by DiGiTY on 2009-01-12
so far I've replaced the power supply (380 watt) with a brand new one (485 watt) and it still kept freezing. Replaced the hard drive and still kept freezing. I ran the computer off the Ubuntu 8.10 Live disc for about 24 hours and while it didn't freeze I'm not sure what the result indicates (or if it was running long enough).

Any other ideas on what the problem could be?

---

