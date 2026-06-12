---
title: "Dell studio 1747 - Multitouch screen , multitouch trackpad"
date: 2010-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by viiiv on 2010-04-18
Hello. I've recently installed ubuntu 9.10 on my dell studio 1747. I cannot enable the multitouch screen, o trackpad, or even a single touch screen.  Does anybody know how to fix this?

THANKS!

---

### Post by Kai Summers on 2010-04-18
OK can you see if the hardware has been detected and if so what driver (if any) is it using. Also do you know what interface type is it using. i.e. is it plugged into a USB bus on the motherboard? Assuming that it has been detected and just needs to be calibrated to function you might want to try  [***touchcal  (0.31)***]("http://touchcal.sourceforge.net/") it isn't really maintained anymore but works. However if there is no driver associated with the hardware, you will need to identify the port that it is using to send out commands. The following **[thread]("http://ubuntuforums.org/showthread.php?t=158666")** should help!

Let us know how you get on or need more help.

---

### Post by viiiv on 2010-05-02
Hi! thanks for your help, and sorry for my late reply. 
I tried to follow the post, but I could not find out where is the multitouch connected. When I ran cat /dev/ttyS0 (1,2,3,etc) i received an error. I also ran the calibration tool, but as i dont know where the "touchscreen" is  connected, I also, received an error.
On the other hand, I try to follow this link  [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23) 
The touchscreen started to work, but It work awfully, and it kept moving by itself, making imposible for me to use the regular mouse/trackpad.
Thanks for your help!

---

### Post by olexiyb on 2010-08-15
Does anybody solve this issue? I have the same awful behavior with random mouse move if I use touch screen.

---

