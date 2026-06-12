---
title: "Mouse problem!!"
date: 2007-03-11
forum: Desktop Environments
---

### Post by moonliter on 2007-03-11
I have some weird problem. My mouse suddenly stop working in ubuntu,but still works in win xp. Please help me to solve this!:confused:

---

### Post by wheels. on 2007-03-11
Let me guess a USB mouse?
stops working less than 2 minutes after logging in.
ya i had that promblem.
I have an ATI. this is what i did to fix it.
I tried turning off legacy USB support in my bios. didnt work.
so then I installed the fglrx driver.
solved my problem

to install fglrx driver
install
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx

config
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

hope this works for you.

---

### Post by moonliter on 2007-03-11
thanks for your help but it is not usb mouse it is PS/2:confused:
There is the cursor in the middle of the screen but can't move

---

### Post by moonliter on 2007-03-11
Problem is solved!!!
It starts to work again after restarting!!!

---

