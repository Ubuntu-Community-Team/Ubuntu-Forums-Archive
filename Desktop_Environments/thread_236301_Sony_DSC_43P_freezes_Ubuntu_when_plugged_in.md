---
title: "Sony DSC 43P freezes Ubuntu when plugged in"
date: 2006-08-14
forum: Desktop Environments
---

### Post by PhilJ on 2006-08-14
Hello all, hopefully someone can help me with this one. My son in law has one of these sony cameras which freezes ubuntu as soon as it is plugged in and switched on. Gtkam doesnt have time to recognise it before everything locks up and a reboot is needed. I have looked thru the forums but cant find anything similar. I tried all the usb ports and logging on as root to run Gtkam but nothing seems to work. works in PTP mode according to Gphoto  Please help my street cred :)


Edit Dapper 6.06
tia

Philj

---

### Post by PhilJ on 2006-08-14
bump

---

### Post by PhilJ on 2006-08-15
Comeon guys ,

 this is not doing my rep any good

:)

philj

---

### Post by PhilJ on 2006-08-15
Comeon guys ,

 this is not doing my rep any good

:)

philj

---

### Post by kostkon on 2006-08-15
What happens when you put the camera in USB mode. Do you get the same thing as in PTP mode?

From experience I know that Sony DSC cameras are not easy with Ubuntu. I tried an DSC-U20 in Ubuntu 5.04 without any results. I was getting something when the camera was in USB mode but I didn't look through this much.

---

### Post by PhilJ on 2006-08-15
Hi, sorry for delay in reply. As soon as the camera is switched on Ubuntu freezes in either mode


Philj

---

### Post by PhilJ on 2006-08-16
bump

---

### Post by PhilJ on 2006-08-23
update of sorts

I got my daughter to drop the camera off here (something I should have done before duh ..)](*,)  I plugged it into my setup and straight away gthumb jumped in to ask permission to import photos. I said ok and libphoto2 searched for the driver PTP mode and off it went no problem. My board has only onboard usb 1.1 and is a via chipset board. I dont know the maker. so am presuming that it has something to do with the usb 2 drivers. I am not sure if their computer has a plugin usb 2 as well as onboard , I will have another go with it tomorrow and report.

Philj

---

### Post by PhilJ on 2006-08-25
problem solved but dont know how.

installed camera in my setup no problem

took  my own camera to my daughters and plugged it in, again no problem

plugged their Sony camera back in and lo and behold it worked !!!

Have no idea why this happened I can only put it down to hardware glitch in the camera itself. I had previously tried it in every usb port and it froze the system every time and yet it worked first time in my system and now it works perfectly

So sorry no idea why it didnt work in the first place :confused: 

Philj

---

