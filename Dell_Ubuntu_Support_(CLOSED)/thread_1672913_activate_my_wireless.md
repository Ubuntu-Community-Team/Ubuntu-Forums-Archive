---
title: "activate my wireless"
date: 2011-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by proteus8 on 2011-01-21
Hello, not English so I translated it in google Language Tools
I'm starting in the world of Ubuntu and I need help to activate my wireless, I have a DELL Vostro 1320 notebook my network card is a DELL WIRELESS 1397 WLAN MINI CARD, and try to make it work with various methods including NDISWREPPER, but I did not good results.
Please help me,
I would not have to go back to windows.
the chip on my card is bcm4310 Broadcom USB CONTROLLER
thank you very much

---

### Post by mikewhatever on 2011-01-22
Hello, and welcome to the forum.
No need for ndiswrapper, just connect an ethernet cable and install the native Broadcom driver from System->Administration->Additional Drivers.

---

### Post by proteus8 on 2011-01-24
Hello again, perform the steps I indicated, I think now the active card
But even that failed to detect my wireless network!
When running on the console: iwlist wlan0 scanning
The screen shows me the following.

 
[FONT=Calibri]proteus8@Vostro-1320:~$ iwlist wlan0 scanning
wlan0 No scan results[/FONT]

---

