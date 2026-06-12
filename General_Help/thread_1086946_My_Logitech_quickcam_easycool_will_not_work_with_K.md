---
title: "My Logitech quickcam easy/cool will not work with Kopete or Amsn Or Skype"
date: 2009-03-04
forum: General Help
---

### Post by Jgryder on 2009-03-04
I have searched and have found no answer. my cam works with XawTV,Ekiga, and Cheese.  I really want it to work with Kopete or Amsn or even Skype.

Lsusb says

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 003 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Nevermind after searching some more I found a translated article and fixed both kopete and skype

here is that article
[http://ubuntuforums.org/showthread.php?t=983471](http://ubuntuforums.org/showthread.php?t=983471)

after doing what it said I increased my contrast to 130-140 range and everything works fine.

---

### Post by meinvateristnein on 2009-03-04
i also have quick cam form logitech but i recently found out that it doesnt have driver support almost at all for ubuntu...... hence why it will only work on program that have there own driver support built in my best advice would be to wait until a better version comes out ..... why would you need to use those programs there are hundred of equivalent program that are better even.....

---

### Post by Jgryder on 2009-03-05
meinvateristnein

"programs there are hundred of equivalent program that are better even..... "  

ok then tell me of one of those programs that are so much better that I can use to talk with my friends on the east coast all I want is to be able to use my webcam and chat with them at the same time. 

I thought I had my webcam issues fixed but it doesn't even send the request to them. :(

---

### Post by ProNux on 2009-03-15
In my case, I got my camera working on Kopete by installing the following

libjasper1
libjasper-dev
libjasper-runtime

You might try to install and see if it works. By the way I am on Ubuntu 8.04 Hardy Heron.

---

