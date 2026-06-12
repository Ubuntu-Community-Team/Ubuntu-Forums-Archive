---
title: "Windows Wireless Drivers"
date: 2009-06-17
forum: General Help
---

### Post by Mark2322 on 2009-06-17
Okay, I am a total noob to Ubuntu transitioning from Windows. I am using a Dell Inspiron Laptop 600m with the Broadcom 4311 wirless adapter. I understand that the native driver needs to be blacklisted so that proprietory drivers can be used. I have gone to the documentation web site to try and install from the terminal but have had no luck( i dont know what I am doing). I was able to get Windows Wireless drivers to install and work until, like an idiot, I tried to put the Laptop remix OS on it. Now have replaced that with 9.04 and cant figure out what I did the first time to get the drivers to work. I really like ubuntu but I really like using my laptop. In order for me to continue using ubuntu I need help and dont want to go back to windows. PLEASE HELP!!! If I can find some help I would gladly reciprocate any info I find like bugs and what not. I want to become a part of the community but have no idea how to do it. Thank you for your time.

---

### Post by Legace on 2009-06-17
Maybe this is what you did:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice))

---

### Post by Java Geek on 2009-06-17
Firstly, you may need to install a tool called Wireless Network Drivers(a GUI version of NDISWRAPPER) off of the ubuntu archives...I realize you need internet to do this, so hardwire your modem into the computer for the time being. Once there, install the Windows drivers onto it and see what happens.

---

### Post by Mark2322 on 2009-06-18
I first installed 9.04 and was able to get the windows wireless drivers GUI to load I guess from the cd. It did say that there were proprietary drivers available for Broadcom but when I try to activate the driver it does nothing. Is that because I dont have the native driver blacklisted right or what?

---

### Post by Mark2322 on 2009-06-18
What I could really use is a descriptive step by step installation procedure. Like I said I am totally new to ubuntu so the free docs website is difficult for me to understand. Basically Im not sure what steps I need to take. I appreciate everyone's feedback

---

### Post by Mark2322 on 2009-06-18
Aslo, what other cool stuff can ubuntu do? I am a musician and have found Ardour GTK2 but again have no idea how to use it. Are there documentation websites for the open source programs available for ubuntu? Plus I would like to get a mentor and really learn how Linux or Unix based systems work. I am not your average idiot user but I am no savont either. So if there is anyone that can help me become a more productive member of the community I would really appreciate it.-Mark-

---

### Post by Mark2322 on 2009-06-23
Okay, after some tinkering around I was able to get them to work. I will try to recite the procedure to the best of my knowledge as I didn't write it down. I first used an ethernet connection and opened the terminal and entered sudo apt-get install ndisgtk. I entered my password for the sudo command and it automatically installed ndiswrapper-utils-1.9. Then I had to blacklist native drivers by entering the following commands in the terminal: 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb"
then entered:
sudo tee -a /etc/modprobe.d/blacklist
Okay then without closing the terminal, I opened another and entered:
 sudo ndiswrapper -i ~/drivers/drivername.inf
Now I had already downloaded the drivers for my wireless card and opened
the .exe file in archive manager and extracted the .sys and the only.inf file 
to a folder on the desktop which I named drivers
So in my case I entered sudo ndiswrapper -i ~/drivers/bcmwl5.inf
then went to windows wireless drivers in system/administration/windows wireless drivers
and chose to install new driver. I pointed it to the .inf file in the folder I named drivers
and installed. It gave me an error message saying that hardware was not present but the windows
wireless drivers window said hardware was present so I rebooted and was able to connect to my gateway
I hope this helps because I know I am not the only on with this problem. However I am using a dell
inspiron so it may not work for everyone but it should point you in the right direction if you are having trouble

---

