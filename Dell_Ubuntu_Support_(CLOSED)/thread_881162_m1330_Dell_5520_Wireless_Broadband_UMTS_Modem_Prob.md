---
title: "m1330 Dell 5520 Wireless Broadband UMTS Modem Problem"
date: 2008-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gregstar on 2008-08-05
I really don't know what to do - I tried the howto from motin [http://ubuntuforums.org/showthread.php?p=5449120]("http://ubuntuforums.org/showthread.php?p=5449120") but my problem is that the modem was working (it was going to dail *99# !)by the first time of initialisation, but my simcard was in my huaweii. So after reboot and putting in the card, gnome-ppp was not recognizing the internal modem. 

I searched for /dev/ttyUSB0 and /dev/ttyUSB1 in dmesg and /var/log/messages and I found it. Also ls -la /dev/ttyUSB* showed me this two serials. But gnome-ppp is telling me after sending ATZ, ERROR.

I hope someone knows the conclusion and is willing to tell me. ;)

---

### Post by motin on 2008-08-11
Try UMTSMon instead - gnome-ppp is not very specialized in handling 3g modems. Here is a guide: [HOWTO: Install UMTSMon (GUI for 3g/HSDPA connections)]("http://ubuntuforums.org/showthread.php?p=5449081")

PS This further comment isn't relevant since you already have /dev/ttyUSB*, but for your inkfo, that HOWTO is faulty... airprime and usbserial should not be used (airprime is becoming deprecated and usbserial can't handle HSDPA data rates). So unload them:
```
sudo modprobe -r airprime
sudo modprobe -r usbserial

```
And instead, use:
```
sudo modprobe option
```
If you don't get your /dev/ttyUSB* back after doing this, go back to using airprime until Intrepid comes out...

---

### Post by Gregstar on 2008-08-13
Hello motin!

Thanks for your answer! I reinstalled ubuntu 08.04.1 and recompiled option.c with my Dell 5520. So now I get the /dev/ttyUSB0 and 1 again. I also installed umtsmon (thanks for the howto, but mention to install libqt3-mt). But umtsmon just gives me SIM Failure :(

Did you just got it work by install umtsmon and connect?

---

### Post by motin on 2008-08-13
Yes, as long as I had /dev/ttyUSB* I have always been able to start UMTSMon and connect without any problems...

Try putting your SIM-card in an ordinary mobile phone and check if you can connect to the internet through there.

---

### Post by Gregstar on 2008-08-14
Before I got the m1330, I used my SimCard in an Huawei E270 without any problems. Yesterday the SimCard worked fine in E270.

But something is really strange. I put the productID in option.c, compile it and cp it to its directory. But the modem is really stupid, because it only understands the command ATI - ATZ or ATD or ATH are not useable.

I have read also, that the Novatel u870 needs to log into the network by using the pin code - I set a pin code, but nothing changed.

It is really infuriatingly :(

---

### Post by Gregstar on 2008-08-14
Really strange. I just reboot the machine, start umtsmon and magically it asked me for a pin (I have turned of PIN für my Huawei to avoid any problems, but I have read, that the Novatel u870 need a pin to login to network) and voilla - I was connected to the Internet!

Thank you very much motin! :D

---

### Post by motin on 2008-08-14
No sweat! Welcome to the world of Ubuntu :)
I added the libqt3-mt note to the guide - thanks! (Did you also go for the 2nd alternative in the guide btw?)

---

### Post by Gregstar on 2008-08-17
No, I did the job with alien - I try to have a "clean" installation ;)

---

