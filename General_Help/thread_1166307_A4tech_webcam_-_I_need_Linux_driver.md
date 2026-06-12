---
title: "A4tech webcam - I need Linux driver"
date: 2009-05-21
forum: General Help
---

### Post by goxi on 2009-05-21
I have A4tech Webcam. Where can I find linix driver for it ? And, is there another way to use it with ubuntu ?

---

### Post by neosofti on 2009-05-21
lspci
lsusb

---

### Post by goxi on 2009-05-21
> **neosofti said:**
> lspci
lsusb
you mean "is it PCI or USB ?" It is USB, or you`re reply is something else ?

---

### Post by goxi on 2009-05-21
O.K. command says: "Bus 003 Device 004: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam"

---

### Post by goxi on 2009-05-21
> **goxi said:**
> O.K. command says: "Bus 003 Device 004: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam"
I`ve found some driver "spca5xx" , but when I pass "make" command , shows to many errors. and I can`t compile it...

---

### Post by cb951303 on 2009-05-21
> **goxi said:**
> I`ve found some driver "spca5xx" , but when I pass "make" command , shows to many errors. and I can`t compile it...

it should be already included in ubuntu, did you try if it works already?

---

### Post by goxi on 2009-05-21
In synaptic I can`t find it. Where in Ubuntu I can find it. When I un-plug and plug my webcam nothing happens....

---

### Post by thelugnut on 2009-05-21
I have the A4 webcam ...Vimcro C-91C.
It works very well with Ubuntu 8.04, 8.10 and 9.04, without me having to do anything.
I just tested it again using the program called "Cheese". You can find and load the program from Synaptic. This webcam has the built in microphone and that works very well, also.

---

### Post by goxi on 2009-05-21
> **thelugnut said:**
> I have the A4 webcam ...Vimcro C-91C.
It works very well with Ubuntu 8.04, 8.10 and 9.04, without me having to do anything.
I just tested it again using the program called "Cheese". You can find and load the program from Synaptic. This webcam has the built in microphone and that works very well, also.
Thank you man !! works fine ):P

---

### Post by cb951303 on 2009-05-22
> **goxi said:**
> In synaptic I can`t find it. Where in Ubuntu I can find it. When I un-plug and plug my webcam nothing happens....

what do you expect to happen?
open a webcam application and check if it works :)

edit: oops, you already figured it out

---

