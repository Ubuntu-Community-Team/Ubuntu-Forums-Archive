---
title: "Wierd automount and usb behaviour"
date: 2008-08-28
forum: Desktop Environments
---

### Post by ocset on 2008-08-28
Hi

I have been running Kubuntu 8.04 (KDE3) for a couple of months now without any problems and suddenly I have a very weird thing happening. The situation below is intermittent and if I were to reboot the machine 10 times kubuntu will be normal 30% and behave as below 70% of the time. I have tried to isolate the problem but nothing is consistent.

1. I have a 3com USB network card that works beautifully with kubuntu but today, kubuntu takes about a minute longer to recognise the card and connect to the network.

2. Point 1 may suggest a USB hardware issue but when I look at the storage media, none of my disk partitions show up as they did before either (before and after pictures attached)

3. Automount also stopped working. The message log shows that the device is being recognised but no automount. I can mount it manually which indicates the devices are ok.

I run WindowsXP and a test version of Kubuntu 8.04 (KD4) on the same machine (dualboot) and neither of them have this problem but I seldom boot them up.. 

Any suggestion are greatly appreciated.

Thanks
O.

---

### Post by ocset on 2008-08-29
Hi

I have found the answer - sendmail.

I installed sendmail 2 days ago and would never have thought it to be the culprit. Could anyone explain why they think this is happening.

When sendmail is installed and I log into KDE immediately when the machine boots up, the problem occurs.If however I wait 5 minuntes and then log in, the problem is gone. (Just for clarity, logging in and then waiting 5 minutes does NOT make the problem go away).

If I remove sendmail from the system, the problem goes away.

Any comments greatly appreciated.

Regards
O

---

### Post by yaztromo on 2008-08-29
It may be worth filing a bug over at launchpad for this.

---

