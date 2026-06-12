---
title: "Using Beryl"
date: 2007-10-10
forum: Desktop Environments
---

### Post by amitabhishek on 2007-10-10
How do I use Beryl on my Ubuntu 7.04? What are the hardware requirements? I have AMD X2 with 1 GB RAM

---

### Post by theCoder on 2007-10-12
Make sure Beryl is installed (either search for beryl in the Add/Remove Applications program or running "sudo apt-get beryl-core beryl-manager beryl-settings" from the commandline).

Then go to Applications -> System Tools -> Beryl Manager

The sys requirements are low (I have half the machine you do, and it runs without a hitch), but I am pretty sure you need to have 3d acceleration configured for your video card for X Windows, and will need to activate it before beryl.

Your mileage may vary depending on your video card, but having an Nvidia FX card, I was able to go to System -> Administration -> Activate Restricted Drivers to almost instantly get 3d acceleration under Ubuntu.

The more seasoned Ubuntu vets can probably offer more wisdom, but this should get you in the right direction.

---

