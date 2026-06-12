---
title: "Ubuntu wireless problem on Dell XPS 15"
date: 2012-04-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Meikrekel on 2012-04-09
I've got a problem with my WiFi: since today my laptop (l502x) is set automatically in airplane-mode. If I uncheck the checkmark for airplane-mode, it will go back to airplane-mode automatically. Because of this I can't connect to my WiFi. 

I've tried 'sudo rfkill unblock all', but that won't work. 
On the internet they also suggested a BIOS-upgrade, but I don't know how to do that because I have removed windows and the file for a bios-upgrade is a .exe. 

In the attachment is a picture of the output of 'sudo rfkill list'

---

### Post by blackpaw on 2012-04-25
it says "Hard blocked" so either you need to flip / push some hardware button (the one that enables/disables the WiFi) or you need to check BIOS for "enable LAN/WLAN" switching and turn it off (business feature of HP to disable having WLAN and LAN on a the same time as this can cause all kinds of weird issues in a LAN.. like asymmetric routing, loops, IP conflicts, etc...)

---

