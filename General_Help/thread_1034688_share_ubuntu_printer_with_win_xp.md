---
title: "share ubuntu printer with win xp"
date: 2009-01-08
forum: General Help
---

### Post by smasterson on 2009-01-08
I have 2 desktops & 1 laptop networked & sharing printer running ubuntu 8.04. I just got an acer aspire one netbook with win xp on it.Could someone please steer me in the right direction to figure out how to share my ubuntu printer with win xp? ubuntu picks up the windows netbook in network, but I can't get windows to see the printer on ubuntu 8.04. Any help would be greatly appreciated. Thanks in advance.

---

### Post by mssever on 2009-01-08
So the printer is physically connected to a Linux box, right? What method of sharing are you using? IPP or Samba? IPP is probably the default. But you'll have to install the Unix printing tools on XP to connect to IPP. I think you can get them in Add/Remove > System software.

Your other option is to share your printer via Samba. This will possibly require a bit of configuration on the Linux box, but once shared any Windows box will be able to use your printer.

---

### Post by cjazz on 2009-01-09
You might want to try [this link.]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")

---

