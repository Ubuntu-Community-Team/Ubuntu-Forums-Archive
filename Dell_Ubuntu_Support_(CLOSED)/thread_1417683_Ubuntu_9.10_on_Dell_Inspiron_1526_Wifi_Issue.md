---
title: "Ubuntu 9.10 on Dell Inspiron 1526 Wifi Issue"
date: 2010-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Drell on 2010-02-27
I used Wubi to install 9.10 on my Inspiron. Now how can I get the WiFi card to work. I've yet to figure out. I am currently going to try using the Ndiswrapper method I heard about to hope it works. I am a noob at this but I love Ubuntu (Used to have 8.10 on my Desktop) So if I can get info on how to make it work. I do have easy access to Wired if it's required, but I prefer wireless. Thanks.

---

### Post by 2hot6ft2 on 2010-02-27
So I'm guessing that the Inspiron is a Laptop since you don't give an actual model. If it's an internal wifi card then in a terminal run
Applications > Accessories > Terminal
```
lspci
```
if you have a usb wifi then use
```
lsusb
```
and post the results so people can figure out what the wifi adapter is you're trying to get working.

---

### Post by gibbylinks on 2010-02-27
Alternatively connect to a wired network then go to "Hardware Drivers" and see if anything is detected. If like my 1501 it detects the Broadcom mini card it will download and install the drivers for you. :p

---

### Post by Drell on 2010-02-28
Thank you Gibbylinks!

I am used to Ubuntu on my old Dell Dimenson 5100 Desktop with wired, but trying to connect my Inspiron Laptop was difficult, but I got my drivers now! I can use Ubuntu at friend's houses and show off my awesome-ness!

---

