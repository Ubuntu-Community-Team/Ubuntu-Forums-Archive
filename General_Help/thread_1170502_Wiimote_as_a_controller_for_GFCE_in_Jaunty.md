---
title: "Wiimote as a controller for GFCE in Jaunty?"
date: 2009-05-26
forum: General Help
---

### Post by cdwillis on 2009-05-26
Has anyone been able to get their Wiimote working as a controller for GFCE in Jaunty? I have installed wminput wmgui and lswm. The mac address I get with lswm is 00:17:AB:2E:E7:E5 and the controller is detected with wmgui. I've also started the uinput module, but when I try to set the controls in GFCE it doesn't detect the controller. Any help is much appreciated.

---

### Post by cdwillis on 2009-05-26
I tried manually starting the uinput module and get this:

cd@mercury:~$ sudo modprobe uinput
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
cd@mercury:~$ 

lsmod lists uinput so I'm not sure if that has anything to do with it. I've also tried mapping buttons in ZSNES but still no input was detected from the Wiimote.

---

### Post by Maheriano on 2010-02-15
When I choose the gamepad and push the buttons, it does detect the controller and set the buttons to what I select but when I play the game it doesn't respond to the buttons at all. So I'm also wondering if anyone has gotten it to work completely.

---

