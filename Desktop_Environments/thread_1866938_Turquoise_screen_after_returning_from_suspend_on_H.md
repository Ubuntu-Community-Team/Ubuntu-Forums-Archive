---
title: "Turquoise screen after returning from suspend on HP Pavilion dv6000"
date: 2011-10-22
forum: Desktop Environments
---

### Post by user790 on 2011-10-22
When I close the lid and come back, ubuntu 11.10 shows a plain turquoise screen with the mouse cursor. At first I thought it crashed but when I type my password it actually logs me in.

If I suspend manually, I have a slightly different behavior: the login screen shows up ok but this time when I log in, there is turquoise all over my desktop and windows.

It is not a major issue as I discovered I could still log with the turquoise screen, however this is unpleasant and a regression from 10.04 whose suspend was working like a charm on this laptop.

---

### Post by user790 on 2011-10-24
Problem solved by selecting "version current" rather than "version 173" of the NVidia driver in System settings>Additional Drivers

---

