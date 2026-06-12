---
title: "Ubuntu freezes at login."
date: 2006-08-05
forum: Desktop Environments
---

### Post by noway on 2006-08-05
I installed Ubuntu 6.06 (Dapper Drake) and when I get to the login screen I can move the mouse for one or two seconds then everything freezes and I have to manually turn the computer off and then on again. I've been able to install 5.10 (Breezy Badger) earlier. Maybe the problem is my motherboard (EPoX EP-8KDA3+ - nVIDIA nForce 3) or graphics card (ATI Radeon 9800 PRO)?

---

### Post by andersja on 2006-08-07
I had this problem when using a poorly supported wifi card & NetworkManager at the same time: login screen would come up, I could start typing for a second or three, then screen would freeze / PC 'hard lock'. I resolved by booting in console mode and sudo apt-get remove the Network Manager packages.

---

