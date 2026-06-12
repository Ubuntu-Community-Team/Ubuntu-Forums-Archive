---
title: "cell phone problems"
date: 2009-06-16
forum: General Help
---

### Post by sandyd on 2009-06-16
I got a major problem here. I currently can't transfer files onto any cell phone. My (two) cellphones require me to connect to the computer, THEN go to the menu and select "Usb mass storage device". When it first connects it is in serial mode. Ubuntu doesn't detect the change to "USB mass storage Device". This works in 8.04 and 8.10.

Can someone help?

---

### Post by Mka on 2009-06-16
I'm using samsung U800 on intrepid to transfer files between the phone and the PC but as far as I know, you cannot (easily) use the memory of the phone. You MUST have a MicroSD card (or whatever relevant card in your case) inserted in your phone. 

If you DO have the memory card inserted, the problem might lie with your ubuntu setup (for example, does the same thing happens when you plug a USB Flash Disk in your PC?). In that case, you may look for the corresponding device in /dev folder. Try this:
```
ls /dev/sd*
```

If you see it there among the output, just mount it, like for example:
```
exo-mount -d /dev/sdb1
```

---

