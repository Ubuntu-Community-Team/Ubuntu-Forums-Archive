---
title: "Dell inspiron 8600 - Wifi and Ethernet problems"
date: 2011-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tyguy609 on 2011-09-14
I recently installed ubuntu 10.4 on my Dell inspiron 8600.  I have been unable to get it to connect to my LAN and the internet.  I have tried both the Ethernet port and Wifi, but neither is working so far.  My hypothesis is that I do not have the needed drivers.  Does anybody know where/how to get the necessary drivers?

---

### Post by mörgæs on 2011-09-15
If you boot a live Ubuntu or Xubuntu 11.04 with internet cable attached, do you get access?

---

### Post by tyguy609 on 2011-09-17
I tried to run 11.4 live from the disk before I installed 10.4, but unfortunately it does not (yet) have enough ram to run 11.4.  I do plan to get more ram so that I can run 11.4 on it, but that may not be for a while.

---

### Post by Megaptera on 2011-09-18
Have you tried using the menu bar on the top panel?
System > Administration > Hardware drivers clicking on that gets me the drivers I need and installs them on my Dell - no other intervention on my part.
Worth a try if not already done?

---

### Post by mörgæs on 2011-09-18
If you are low on ram, I would recommend Xubuntu or Lubuntu 11.04.

---

### Post by varunendra on 2011-09-18
> **mörgæs said:**
> If you are low on ram, I would recommend Xubuntu or Lubuntu 11.04.
+1
They are lighter versions with newer kernel, so have better chance of having appropriate drivers if that is your case.

If you wish to try troubleshooting with 10.04, please enter the following commands in a terminal and post their outputs here:
```
sudo lshw -C network
ifconfig -a
iwconfig
rfkill list all
```

---

### Post by tyguy609 on 2011-09-18
I figured out the problem with my WIFI.  When watching my laptop boot up, I kept seeing something about Firmware file "b43legacy/ucode4.fw" right before Ubuntu would start loading.  I went to the address it specified and followed the instructions to install the necessary firmware for my Broadcom WIFI card.

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware")
and
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")

Now I will see if I can get my Ethernet card to work.  Now that I have internet on it though, Ill mark this as solved.

---

