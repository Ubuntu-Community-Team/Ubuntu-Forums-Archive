---
title: "digital camera question"
date: 2006-08-18
forum: Desktop Environments
---

### Post by evillawngnome on 2006-08-18
I picked up a TINY little usb camera at walmart today for $15. THe brand is digital concepts. In searching for a pic, i found this:

[http://www.amazon.com/gp/product/B0009IRUZQ/ref=nosim/102-1249237-1976947?n=502394](http://www.amazon.com/gp/product/B0009IRUZQ/ref=nosim/102-1249237-1976947?n=502394)

Looks like its a generic little cam. It has 16mb internal SDRAM. Looking at /var/log/messages, i can see the kernel detecting it. In fact, this is what it says:
```
Aug 18 19:47:44 localhost kernel: [17181488.788000] usb 1-1: USB disconnect, address 4
Aug 18 19:47:47 localhost kernel: [17181491.864000] usb 1-1: new full speed USB device using ohci_hcd and address 5
```

Ideas on how i can access this litle cam?

---

### Post by zxee on 2006-08-18
First try unplugging and re-plugging in the camera. If that doesn't work then 
take a look at the 2nd page of this thread: [http://www.ubuntuforums.org/showthread.php?t=80762&page=2&highlight=digital+camera+mounting](http://www.ubuntuforums.org/showthread.php?t=80762&page=2&highlight=digital+camera+mounting)
Installing gtkam > sudo apt-get install gtkam seems to be a fix for some people.

---

