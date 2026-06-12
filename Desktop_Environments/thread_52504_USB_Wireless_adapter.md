---
title: "USB Wireless adapter"
date: 2005-07-28
forum: Desktop Environments
---

### Post by noobuntu on 2005-07-28
Hey guysi have Kubuntu 5.0.4 installed and am using a speedstream 1022 wireless usb adapter. now ive looked everywhere and have read that others have installed and used this hardware successfully. can anyone tell me how they did this (if they did) im a noob and need the steps. Please help...a laptop with out wireless network is nothing but a desktop :mad:

---

### Post by noobuntu on 2005-08-02
WOW!, no answers? no links? no yodaisms?  lol....i guess this is as hard as i thought....

Come on people...anyone? Pleeeeeeeeeaseeeee!!!  I need help lol

---

### Post by t2kburl on 2005-08-03
Try posting this question under Networking

---

### Post by stjepan on 2005-08-03
sudo apt-get install wireless-tools
sudo apt-get install ndiswrapper
This should install ndiswrapper and wireless-tools
Then get driver for your adapter or download it somewhere
After that do:
ndiswrapper -i your_driver.inf
modprobe ndiswrapper
And now everything is installed. Now just configure it. Ndiswrapper documentation will help you.
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Good luck!

---

