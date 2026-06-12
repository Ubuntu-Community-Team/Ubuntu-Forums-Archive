---
title: "Latitude 630 and Feisty"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by jtrevorjones on 2007-07-20
I am a total newcomer to Linux and  have installed Ubuntu 6.1 (Edgy).  I can't get the win-modem to work ( I have to go back to Win 2000 to post this) but otherwise I'm getting on well with the learning curve.  However - I have tried updating to Feisty using two different versions and with both I get the same result.  The first menu screen comes up but when I try to install there is a brief flurry of DVD activity and then the system seems to hang but after a while I get a series of messages:
Buffer I/O error on device fd0 logical block 0
Buffer I/O error on device fd0 logical block 1
Buffer I/O error on device sr0 logical block 0
Buffer I/O error on device sr0 logical block 1
Buffer I/O error on device sr0 logical block 2
etc
etc
I have tried to search the existing threads but I haven't seen any similar problems so please forgive me if I am treading old paths.
tia

---

### Post by magiceraser06 on 2007-09-21
You can try installing with the option BOOT: noapic

if your getting Buffer I/O errors, it may mean that your system is having IRQ conflicts and/or trouble allocating the space.  By disabling APIC, it may allow you to do an install.

i had something similiar, not very, but that helped.

Any of the other gurus out there concur?

---

