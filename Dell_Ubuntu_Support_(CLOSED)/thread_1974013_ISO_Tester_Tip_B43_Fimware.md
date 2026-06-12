---
title: "ISO Tester Tip B43 Fimware"
date: 2012-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nm_geo on 2012-05-05
If you have the b43 driver and firmware working on your computer and say your running Natty.. and you want to try Precise .. make a copy of the b43 folder in /lib/firmware.

I do quite a bit of iso qa-testing on my Dell D620 and here is a little tip I have picked up along the way.

1) Go to            >  /lib/firmware
2) Copy Folder > b43 
3) Save it to a USB drive

Now when you try Ubuntu, Lubuntu or Xubuntu before installing go to try Ubuntu.  Then stick in your USB (flash drive) and copy the b43 folder to your desktop. Now we can go to the terminal:
 
4) Get to the Desktop >```
 cd Desktop
```5) Now we need to write the b43 folder to /lib/firmware
6) In terminal type ```
sudo mv b43 /lib/firmware
```7) Wifi light should come on and you can sign in to your access point.
8) If you decide to install the version you are testing Go right ahead you have wifi connected. Now when the installation is completed and you reboot.  Go through the same process to get to get the b43 firmware folder in /lib/firmware.  Next time you reboot it will be working (automagically)  Have Fun  :p

I have used this same method for testing Natty, Oneric and Precise and rarely do I hook up to an ethernet cable. Of course it does require that you have a version working with b43 driver and the correct b43 firmware.

---

### Post by carl4926 on 2012-05-05
I can confirm this works. I do it all the time

---

### Post by bayouoldguy on 2012-05-23
nm_geo,   Thanks for this tip. I have been trying to perform this
on a Dell D620 to check out 12.04LTS. It was very trying to hook up a hard wire & download the B43 firmware each time I wanted to look around, using the wireless. I am running a dual-boot 10.04LTS & Windows Vista on the Dell.
Next question: can we also copy a folder from the 10.04LTS wireless
connection, ( ie. router settings ), & eliminate one more set up step ?
Where are the wireless/router settings in 10.04LTS ?.
........"G"

---

### Post by Comodín on 2012-09-11
Every time when I boot up on my Dell Inspiron 1525, I have to do a "sudo modprobe b43" to activate the network card. It won't give me wireless connection without this. Any suggestions on how to have it activated from boot?

---

