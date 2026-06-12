---
title: "Reboots instead of shutdown."
date: 2015-01-09
forum: Desktop Environments
---

### Post by fall2 on 2015-01-09
Lubuntu 14.04
OS reboots through shutdown commands and normal logout shut down option. 
I reinstalled my OS and it still reboots.
Only way I can shut down is to hold down the power button.

Problem started when I uninstalled power manager, I reinstalled it right away but it just reboots over and over now.

---

### Post by raja.genupula on 2015-01-09
> [COLOR=#000000]OS reboots through shutdown commands[/COLOR][COLOR=#000000]
whats the command you are using ?[/COLOR]

---

### Post by fall2 on 2015-01-10
Tryed sudo poweroff and I think it was sudo shutdown and it reboots.

---

### Post by jeremy31 on 2015-01-10
Can you post the terminal output of ```
lspci
``` as there is a known bug with the xhci driver that can cause this with certain intel chipsets

---

### Post by fall2 on 2015-01-10
um I don't know how to copy the terminal text but I have a 82852/82855GM integrated graphics device.

---

### Post by jeremy31 on 2015-01-10
You can highlight by clicking and dragging with the mouse/touchpad and then right click to copy
Bug report [https://bugzilla.kernel.org/show_bug.cgi?id=66171](https://bugzilla.kernel.org/show_bug.cgi?id=66171)

---

### Post by mörgæs on 2015-01-10
If it's the same hardware as your [other thread]("http://ubuntuforums.org/showthread.php?t=2258324&page=2&p=13195431&viewfull=1#post13195431") please link to it. Gives people a better foundation for answering.

I would try a fresh install of 14.10 even though we don't have hard proof that it's solved there.

---

### Post by fall2 on 2015-01-10
> **mörgæs said:**
> If it's the same hardware as your [other thread]("http://ubuntuforums.org/showthread.php?t=2258324&page=2&p=13195431&viewfull=1#post13195431") please link to it. Gives people a better foundation for answering.

I would try a fresh install of 14.10 even though we don't have hard proof that it's solved there.

yeah its the same.

I tryed a fresh install of Lubuntu 14.04, which I thought would fix it but it didn't and I just don't know now.

---

### Post by fall2 on 2015-01-10
The problem started when I uninstalled xfce4-power-manager. sudo uninstall xfce4-power-manager, I then put in sudo install xfce4-power-manager (didn't fix it). Then I reinstalled Lubuntu 14.04 to try and fix it(didn't fix it).

---

### Post by mörgæs on 2015-01-10
I suggested a fresh install of 14.10, not 14.04.

---

### Post by fall2 on 2015-01-10
> **mörgæs said:**
> I suggested a fresh install of 14.10, not 14.04.

Well since I don't have a usb memory card/dvd burner or dvd-r's on hand i'll have to wait on that untill I get one to use. I do have cd-r's but L14.10 is 705mb, ](*,) .

---

### Post by mörgæs on 2015-01-10
Using a [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") one can install 14.10 from CD.

---

