---
title: "It is an awesome feeling"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Name on 2005-10-14
Ive been working with computers for years, 99% in windows or dos. 

I fired up the laptop (dual boot) into Ubuntu and got an error with Xserver. I checked the output error, there were problems with xorg.conf, so I sudo nano into it and start poking around. Found a typo corrected and rebooted. Still no gui and still errors in xserver. error mentions that something was referencing configured mouse, so I nano it again and find the ref. I then put 2+2 together and get 4 and change it to mouse.usb, which is what it should be looking for as I  made some changes yesterday to my mouse to make all the buttons work...

rebooted and back into the gui. Im a linux nub and this is the first real problem ive had where I actually figured it out with out any help. 

its a great feeling.

---

### Post by Stormy Eyes on 2005-10-14
Welcome to Ubuntu, man.

---

### Post by darkmatter on 2005-10-14
^What he said ;)

---

### Post by 11hjpphty76lkjj on 2005-10-14
I never edit the xorg.conf file directly.  I use a USB hard drive to boot from and when I boot from a different machine I run dpkg-reconfigure xserver-xorg and it fixes it right up.  Not sure if that might be easier for you in the future or not.

Ubuntu rules!

:-({|= 

Aaron

---

