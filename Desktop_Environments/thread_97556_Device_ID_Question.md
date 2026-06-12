---
title: "Device ID Question"
date: 2005-12-01
forum: Desktop Environments
---

### Post by bananaman on 2005-12-01
Hi... I tried searching the forums and could not find an answer...

Im trying to run ndiswrapper and is asking me for the the device id (PCIID) of my wireless network card... the problem is that i dont know where to look for the device id... i tried the device manager and i dont see it there...

any help will be greatly appreciated...thanks

---

### Post by jalanbuntu on 2005-12-01
what is your wireless card type??????
if it's usb you can try 
```
lsusb
```

if it's pci you can try
```
lspci
```

---

### Post by bananaman on 2005-12-01
hey thanks dude..
i got it working! wireless for everbody! woohooo..
anywho... thanks

---

### Post by rpjanaka on 2008-04-25
I want to get the name of my USB webcam as it is listed in /dev directory. Is there a way to get it...?

I think that I could use the device ID which is listed by the **lsusb **command.

Please help me to do this...

---

