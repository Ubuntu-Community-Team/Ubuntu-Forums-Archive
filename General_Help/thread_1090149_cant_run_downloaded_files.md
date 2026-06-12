---
title: "cant run downloaded files"
date: 2009-03-07
forum: General Help
---

### Post by r0k on 2009-03-07
i am new to the linux world and need some help!  i cant seem to run any file that i download!  for example i tried to install the driver for my nvidia geforce 7800 gt pro and this is the message i received

Could not open the file /home/jake/Desktop/NVIDI…Linux-x86-180.29-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
===========================================

Please help!!

---

### Post by taurus on 2009-03-07
You need to run it from a terminal, not double-clicking it.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
ls -la
```

Have you looked in System -> Administration -> Hardware Drivers to see if your nvidia graphic card is on the list and whether there is a driver for it?

---

### Post by r0k on 2009-03-07
thank you i will try that now!

---

### Post by r0k on 2009-03-07
yes there is 2 drivers listed.  i tried the one that is recommended but its still saying the driver is not activated!

---

### Post by RedSingularity on 2009-03-07
> **r0k said:**
> yes there is 2 drivers listed.  i tried the one that is recommended but its still saying the driver is not activated!

Restart the computer?

---

### Post by r0k on 2009-03-07
scratch that i tried it again and it worked! thank you very much for your time

---

