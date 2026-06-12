---
title: "Computer shuts down without warning"
date: 2008-08-06
forum: Desktop Environments
---

### Post by bluefloyd8 on 2008-08-06
Hello,
I am running Ubuntu on a newly built PC. It was all running great and then I had to ship my computer home from school. When I unpacked it, it no longer works. 

After anywhere from 15 seconds to 4 minutes, the computer will just shut off as if someone unplugged it. I am assuming this is a hardware problem; perhaps an overheat protection. 

Any ideas on why this is happening would be appreciated.

Specs:
Intel Core 2 Duo
ASUS P5N-E SLI LGA 775 NVIDIA nForce 650i SLI ATX Intel Motherboard
WD 500GB hard drive
Some old ATI video card (PCI)

---

### Post by silkstone on 2008-08-06
It could well be an overheating issue - perhaps a fan cable came unplugged when it was moved.

If you take a look inside, there should be at least two fans plugged into the motherboard. One is the CPU fan and the other is the case fan. Check that these are both firmly connected (turn the mains power off first and unplug the machine!). Also make sure that the CPU fan assembly is secured firmly to the motherboard and is in contact with the CPU. If it has come loose, you'll have to clean everything up and apply some thermal paste/grease before reassembling.

Provided you don't touch anything inside, you can boot up and make sure that all the fans are working. In addition to the two already mentioned, there will also be a fan on the graphics card.

---

### Post by tamoneya on 2008-08-06
I agree with the heating issue.  I recommend typically just taking a can of compressed air to the computer.  Cleaning out dust is a great way to increase air flow and heat convection.  Also install some sort of monitoring application so that we can confirm that the computer is running hot.  I recommend lmsensors + conky.

---

### Post by jrasmussen0 on 2008-08-06
Also look for bulging capacitors.  I had a Dell model a few years back that kept shutting off after clicking something.

---

### Post by y@w on 2008-08-06
Is the machine hot? Is the heat sink on the graphics card hot to the touch? Otherwise I'd try changing out the power supply.

---

