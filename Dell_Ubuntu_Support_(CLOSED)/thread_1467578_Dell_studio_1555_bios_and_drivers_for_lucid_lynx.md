---
title: "Dell studio 1555 bios and drivers for lucid lynx?"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maximus.bobba on 2010-04-30
hey, has anyone found the right bios and ati driver combination for lucid lynx?

---

### Post by xenon401 on 2010-05-01
I have a Dell 1555 Studio, too. When I run Lucid Lynx from VirtualBox, I get the purple UI screen, select "try ubuntu without any changes to your computer", then I get a black screen with an "_" in the top left corner. any suggestions?

---

### Post by P4man on 2010-05-01
If you run it in virtualbox, it doesnt matter what hardware it runs on, ubuntu only sees the virtual machine. You probably need to update virtualbox to run lucid

---

### Post by P4man on 2010-05-01
> **maximus.bobba said:**
> hey, has anyone found the right bios and ati driver combination for lucid lynx?

You probably want the latest bios. As for driver, no clue. I take it the default opensource driver isnt working well?

---

### Post by xenon401 on 2010-05-01
Just one more thing, when installing Ubuntu in a VirtualBox, you can use the install icon and follow the on-screen instructions and it will not mess around with your physical hard drive. Since it is all virtual, it acts as if it is on it's own hard drive, correct?

---

### Post by P4man on 2010-05-01
correct (if you boot the cd /iso in virtualbox), but may I ask you to start your own thread about installing ubuntu in virtualbox should you have further questions?

---

### Post by xenon401 on 2010-05-01
I understand the process now. I already have been using Ubuntu 9.04 on my physical hard drive and just wanted to know basically if it applies the same concepts in VirtualBox.

---

### Post by maximus.bobba on 2010-05-01
well this morning i used the hardware driver program in the system menu to update the ati drivers. after updating the ati driver, everything was seemed to be in fine order. catalyst was working fine. but then i went on to the ati website and installed the latest driver for linux with a release date 2010. 

completely messed up the ui after that. none of the desktop effects were working, a lot of lag... so i guess allowing the hardware driver program to choose the driver is the best option...

---

### Post by maximus.bobba on 2010-05-01
And if that wasnt enough, i was messing with the cairo docks theme and animation settings with the new druvers. that badle affected the speeds.

---

### Post by warri0r on 2010-05-03
just install the proprietary driver listed in the hardware drivers application. It works flawless with lucid at my end.

---

### Post by maximus.bobba on 2010-05-09
thats exactly what i did. i used the hardware driver app but after a while, messing with the 3d effects or playing a HD movie tends to slow down the pc :(

---

