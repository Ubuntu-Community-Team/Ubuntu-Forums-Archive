---
title: "Inspiron 1521 enabling broadcom 4311 (ver 1)"
date: 2009-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pen16 on 2009-11-08
Hi, i have been attempting to get a friends laptop to work to the best of its ability.  I can get the graphics card working and the audio and everything but the Wifi.  I know there are freakin' thousands of threads about the stupid broadcom card support and i have been doing research for this very subject for weeks on end.  I tried the drivers that ubuntu suggested both the b43 and the sta drivers under the hardware drivers app but none work.  I evened tried some crazy stuff i found on a page, and got the network manager to allow wireless but the card itself still isn't working.  I believe the closest i have come is with ndiswrapper.  But everytime i install the proper windows driver suggested to me on the almighty list the windows driver app tells me it is unable to tell if the card is present.  So i reinstalled pciutility and still haven't gotten it to work.   I feel like im really close but im ready to pull my hair out and my buddy is losing patients.  I really would appreciate the help.

---

### Post by dvlchd3 on 2009-11-08
b43xx (especially that early of a card) should be rather well supported in Ubuntu now.  I have not had to use ndiswrapper for my bcm4318 card since 7.10 (maybe 8.04, not really sure...).

There are serveral "tricks" (if you can call them that) though.

First, try to trace your steps back and get rid of ndiswrapper.  Because it has been so long since I've used it, I can't begin to tell you how.  I'm assuming a simple sudo apt-get uninstall ndiswrapper will suffice, but I'm not sure.  You may also have to do some rmmod to get rid of any modules you installed with modprobe.  Also, if you added something to the blacklist, take it out!

Next ensure the fwcutter package is installed:

```

sudo apt-get install b43-fwcutter

```

It sounds like it is, but just to make sure.

Also, it is sometimes helpful to install/reinstall the firmware.  I don't know why this tends to break spontaneously like it does, but...it does.

```

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```

That is all I have ever had to do since 8.04 to get my b43 card to work.  That last script seems to be the key to solving a lot of issues.

---

### Post by Pen16 on 2009-11-08
well i blacklisted b43, b43legacy and some other things and i do not know how to undo that

---

### Post by Pen16 on 2009-11-08
i installed it and it downloaded and did all its work and as far as i know no errors and i even popped in the second code and it all workied fine.  Now i just need to unblacklist the crap i blacklisted.  I wish there was a physical list and checks but i don't suppose they have those on linux.

---

### Post by dvlchd3 on 2009-11-08
I'm going off another guide I just found, but give this a try:

```

sudo gedit /etc/modprobe.d/blacklist

```

Find the entries: (probably at the very end of the file)
```
blacklist b43
blacklist b43legacy
```
and delete them.  Save, close.  Reboot.

---

### Post by Pen16 on 2009-11-08
Cool man, you saved my butt.  Now thats it not blacklisted should i restart and see if it works

---

### Post by Pen16 on 2009-11-08
So utlimatly i am going to be using the hardware drivers app and get either b43 driver or the sta driver to work right. I have tried both and niether seem to work

---

### Post by dvlchd3 on 2009-11-08
You shouldn't need to enable anything in hardware drivers.  The command to install b43-fwcutter should have taken care of that.

This may seem dumb, but does the laptop have a wireless switch.  If so, is it toggled to the on position?  (Occam's razor :D)

Does the laptop have a wireless light.  If so, is it on?  If not, is it on after you type the following command:

```

sudo ifconfig wlan0 up

```

Assuming the wireless light has come on (if it exists) can you see any wireless networks with this command?
```

sudo iwlist wlan0 scanning

```

If so, this is an issue with NetworkManager.  To connect to a wireless network without NetworkManager:

```

right-click the network icon, uncheck enable networking to disabled NetworkManager

sudo ifconfig wlan0 up
sudo iwlist wlan0 scanning
(Note the ESSID of the network you want to connect to:)
sudo iwconfig wlan0 essid "ESSID from above"
sudo dhclient

```

If this allows you to connect, we need to start diagnosing NetworkManager because doing the above everytime is rather anonying...

---

