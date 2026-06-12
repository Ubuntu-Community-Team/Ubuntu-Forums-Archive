---
title: "are there any webcam experts?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-31
I have tried many suggestions and many different times to get my webcam working under Ubuntu. It is a logitech. Is anyone willing to take a shot at getting it to work? I want someone with Linux expierence and someone who has got his or her own webcam working to help me get mine working by using remote desktop to see my screen with VNC? VNC is already set up. Contact me by instant messenger or email or any other way. All of my information is on my profile.

---

### Post by meng on 2006-08-31
I am not an expert. But I am sure you will have to specify which Logitech webcam you have, as there are lots and some can be set up and some not.

---

### Post by fakie_flip on 2006-08-31
> **meng said:**
> I am not an expert. But I am sure you will have to specify which Logitech webcam you have, as there are lots and some can be set up and some not.

The exact model is unknown, but that's not important. I'm not asking for more suggestions. I am asking if there is anyone willing to try to get it working using VNC.

---

### Post by TobbeR on 2006-08-31
Hi

I have 3 different webcams working and yes I am an expert. Easy enough because there's only one secret about webcams and thats the driver.

How to find the driver:

Attach the cam
In a terminal type sudo lsusb, write down the ID, ie in my case it's 046d:08b2 meaning Logitech QC Pro 4000

Search for a driver on this site [http://www.qbik.ch/usb/devices/search.php](http://www.qbik.ch/usb/devices/search.php),
use the ID in the search engine, it's the only way to identify the cam (or any other USB device)
If it's not there, search Google

Install the driver, instructions will be found on the site of the driver.

Thats it!!   Try it with Camstream or Camorama from the repo's

And if no driver is available?
Bad luck, you can wait and hope someone will write a driver in the future or you can buy a new cam
TobbeR

---

