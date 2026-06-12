---
title: "Wireless Connection on Dell Inspiron?"
date: 2009-12-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ryan45419 on 2009-12-19
when i get onto ubuntu and try to connect to a wireless network it doesnt find any. can someone help me??

---

### Post by michael37 on 2009-12-20
> **ryan45419 said:**
> when i get onto ubuntu and try to connect to a wireless network it doesnt find any. can someone help me??

Go into System->Administration->Hardware Drivers and enable what it suggests.  I bet the driver will be Broadcom STA.

Given a non-open-source nature of these drivers, they cannot be enabled by default in free software.

---

### Post by England on 2009-12-22
I have the same problem except when I try to install the driver, it asks me for the administrator password, which I enter in, and then the driver installation box pops up and almost immediately disappears.  It doesn't install and I cannot connect to the internet.  Also, when I search for drivers, it doesn't detect the NVIDIA drivers it did when I used the Live CD. Any help?

---

### Post by mikewhatever on 2009-12-22
> **England said:**
> I have the same problem except when I try to install the driver, it asks me for the administrator password, which I enter in, and then the driver installation box pops up and almost immediately disappears.  It doesn't install and I cannot connect to the internet.  Also, when I search for drivers, it doesn't detect the NVIDIA drivers it did when I used the Live CD. Any help?

You are having a chicken and egg situation, since you need internet connection to download the driver, but need the driver to establish the connection. The same goes for nvidia. Anyway, try the link below, it shows how to get the Broadcom STA wireless driver from the installation cd.

---

### Post by England on 2009-12-22
Ok.  I didn't have the patience to read through all of the text on the link but I found a thread addressing the issue I had.  If you put in the Live CD, open it, click on the pool file, open up the b file, install the package, and then download the Broadcom STA driver, it will work.  My computer still cannot detect the NVIDIA drivers.

---

### Post by mikewhatever on 2009-12-24
> **England said:**
> Ok.  I didn't have the patience to read through all of the text on the link but I found a thread addressing the issue I had.  If you put in the Live CD, open it, click on the pool file, open up the b file, install the package, and then download the Broadcom STA driver, it will work.  My computer still cannot detect the NVIDIA drivers.

OK, let's install the required packages manually. Can you post the output of the following commands first:

cat /etc/lsb-release

lspci | grep -i nvidia

---

### Post by aydee on 2010-04-22
Um, have you tryed installing the wirless driver with the ubuntu cd in the drive?? That worked on my Dell LATITUDE

---

