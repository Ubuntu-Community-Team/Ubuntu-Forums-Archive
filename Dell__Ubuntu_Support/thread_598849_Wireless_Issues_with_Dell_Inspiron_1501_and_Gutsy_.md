---
title: "Wireless Issues with Dell Inspiron 1501 and Gutsy Gibbon"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by Karant on 2007-10-31
I just tried installing Gutsy Gibbon on my Dell Inspiron 1501 and it does not detect my wireless internet and does not connect to it manually, or any connection for that matter Is there a knwon fix.

---

### Post by dacap06 on 2007-10-31
Try using this howto:  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by erichill on 2007-11-01
> **Karant said:**
> I just tried installing Gutsy Gibbon on my Dell Inspiron 1501 and it does not detect my wireless internet and does not connect to it manually, or any connection for that matter Is there a knwon fix.

In Gutsy all you have to do is first  to connect to a wired internet connection,
Click System-Administration-"Synaptic Package Manager"-Settings-Repositories-Ubuntu Software
Make sure that all the boxes are ticked
Click on Close, then on the Reload button.
Exit Synaptic

Now Click System-Administration-Restricted Driver Manager
Tick the box labeled "Firmware for Broadcom 43xx chipset family"
Download the firmware as per the instructions on-screen.

Voila, your wireless connection should start.

Good luck

Eric

---

### Post by ankghosh on 2008-03-29
I'm Using a Dell E1505.I tried using the ndiswrapper method but had to do it on every start-up to switch on the wifi.When i use resticted drivers to download the required firmware i get the error that the url is invalid:

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

Is there an alternative place i can download this from?or is there any other way to make th wifi work????

---

### Post by DanseNoir on 2008-04-12
> **erichill said:**
> In Gutsy all you have to do is first  to connect to a wired internet connection,
Click System-Administration-"Synaptic Package Manager"-Settings-Repositories-Ubuntu Software
Make sure that all the boxes are ticked
Click on Close, then on the Reload button.
Exit Synaptic

Now Click System-Administration-Restricted Driver Manager
Tick the box labeled "Firmware for Broadcom 43xx chipset family"
Download the firmware as per the instructions on-screen.

Voila, your wireless connection should start.

Good luck

Eric

THANK YOU!  THANK YOU!  THANK YOU!

If you only knew the trouble I've gone through trying to get my wireless to work on Ubuntu!  I've gone through three tutorials with no luck and the solution ends up being so amazingly simple! :)

---

### Post by kelvingeorge on 2008-04-15
I have been trying for days with little sleep. Thank you verrrrrry much. Thank you.

---

