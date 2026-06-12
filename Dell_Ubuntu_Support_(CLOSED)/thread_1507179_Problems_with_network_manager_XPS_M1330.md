---
title: "Problems with network manager XPS M1330"
date: 2010-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ognyang on 2010-06-11
Hey folks,

I have some problems with the network manager.
2 or 3 days ago my system updated and after these update something strange is happening with my network manager. I have to wait about 10/15 minutes my manager to load. For example when I start my machine the os is loading for 6-7 sec. and after 15 to 20 minutes I can access my NM(network manager). When I try to open it from the admin menu the window is showing but it freezes. But the interesting thing is that if I plug the lan cable in the interface I have an access to internet.
I tried to update the manager but no success. Also I tried to connect with WICD network manager but it won`t authorize my password with WPA1/2 encrypting. 

It was kind a difficult to explain but I hope you understand me :)
My ubuntu version is 10.04

---

### Post by Ichido on 2010-06-11
My Dell 1525 was having the same problem so....
I installed Wicd and boosted my Wifi Router's Signal to Extended Range and so far so good.
I am running NM and Wicd at the same time. 
I use WPA and MAC filtering.

Also I created a Desktop Launcher.
Type: Application in Terminal
Code: sudo ifconfig wlan0 up

---

### Post by ognyang on 2010-06-11
> **Ichido said:**
> My Dell 1525 was having the same problem so....
I installed Wicd and boosted my Wifi Router's Signal to Extended Range and so far so good.
I am running NM and Wicd at the same time. 
I use WPA and MAC filtering.

Also I created a Desktop Launcher.
Type: Application in Terminal
Code: sudo ifconfig wlan0 up

Hey I also use WPA2 and MAC filtering but i can`t still validate my password with WICD. It says me "wrong password".
What`s the deal with this launcher?

This is embarrassing! 1st I have to wait 20 minutes to connect via wifi and after that the stupid keyring won`t store my password and i have to type it every single time!

---

