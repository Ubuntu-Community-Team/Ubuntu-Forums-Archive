---
title: "xbox 360 controller help"
date: 2012-03-02
forum: Gaming &amp; Leisure
---

### Post by Cyracus on 2012-03-02
First off I'm very new to linux so I have a lot of trouble figuring out the terminal program. 
What I'm trying to do is get my xbox 360 wireless controller working on ubuntu 11.10. I have a wireless receiver plugged into a usb 2.0 port and in xpadder running through wine it appears to work fine, but outside xpadder it doesn't work in anything, and without xpadder it does nothing and i can't even see if it's reading my button presses.

I've seen a few guides but they were either dated or I just couldn't understand them. here is a link to one: [http://ubuntuforums.org/showthread.php?t=1919590](http://ubuntuforums.org/showthread.php?t=1919590)  not really a guide but I've tried what it says in there but it didn't help. if you want me to post a readout from my terminal please give me the script necessary to get the readout, like I said I'm new to linux and don't really know what I'm doing despite trying to learn for the past month. Any help would be appreciated and if any other information is needed please just ask.


edit:  followed the instructions here [http://ubuntuforums.org/showthread.php?t=1513036&highlight=xbox%2C+controller]("http://ubuntuforums.org/showthread.php?t=1513036&highlight=xbox%2C+controller") but don't know how to map the keys or anything. this was the final readout 
Controller:        Microsoft Xbox 360 Wireless Controller
Vendor/Product:    045e:0291
USB Path:          003:003
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event5


X1:  3328 Y1:  1026  X2:    73 Y2:    -8  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0

I don't understand much except that it can see my xbox controller.



Think I have it working now. pcsx sees it and let me map it in, though it crashed shortly after. but that's something else. followed the instructions here: [https://help.ubuntu.com/community/Xbox360Controller#Troubleshooting](https://help.ubuntu.com/community/Xbox360Controller#Troubleshooting)   even though I have kernel version 3.0.0 or something like that (saw it but didn't note exact number) hope this can help someone else

---

