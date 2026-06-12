---
title: "[Lubuntu] Power Meter stalls / gives inaccurate info"
date: 2014-07-19
forum: Desktop Environments
---

### Post by whyigotta on 2014-07-19
I just got a new battery for my labtop. I plugged it in and it seemed to be charging normally so I was delighted, the time it gave before being fully charged fluctuated rapidy, changing from 6 hrs 40 mins to 1 hr 20 then to 30 mins in a very short time. But the percentage seemed accurate so I ignored it. Then it got to 97% and seemed to stick there, though I left it for quite a while. Eventually I plugged it out and let it deplete. Anyway, the next time i charged it, it got to 55% and stayed there for about half an hour. I figured something was up so I plugged it out and it stayed on 55% until the computer shut down from lack of battery. I plugged in, got it running again and now the battery is stuck on 64% and says there's 40 minutes left until fully charged, when plug it out,it says there 40 minutes left until it's fully empty but the percentage doesn't change. To clarify, it accurately says wheter the AC is plugged in ot not, but doesn't accurately reflect the percentage charge.

TL;DR My power meter in the notification tray doesn't accurately say what percentage power is in the battery, instead getting stuck at seemingly random percentages and not changing.

I have Lubuntu 14.04 on a Dell Latitude D500.

---

### Post by tgalati4 on 2014-07-20
The power meter has a learning algorithm.  It won't be accurate until several charge/discharge cycles.  So save your work when your battery gets weak, then play a game until the battery gets really low.  Some folks recommend getting low enough to cause a sleep cycle or shutdown.  Either way, you need full charge/discharge cycles for the meter to become accurate.  After that, you will have some confidence about how much battery life you have left.

---

