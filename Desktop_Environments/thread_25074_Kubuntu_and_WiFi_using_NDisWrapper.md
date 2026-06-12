---
title: "Kubuntu and WiFi using NDisWrapper"
date: 2005-04-09
forum: Desktop Environments
---

### Post by batteryacid on 2005-04-09
Is there an issue that kubuntu has with using wireless networking? I'm unable to use my wireless connection, but eth0 works fine. Some details: 

The laptop is a dell inspiron 8200 with a broadcom wireless card (uses bcmwl5.inf with ndiswrapper). i had this working in warty under gnome before. I first installed the ndiswrapper-utils package from kynaptic. then:

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo iwlist wlan0 scan

and i get "no scan results" 

I've also tried configuring using kwifimanager, but some searching on the boards revealed that some people had better luck using the gnome configuration toolkit, so i got that too and tried using those tools. Still i get no results. i've also tried manual configuration:

sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid Network 
sudo iwconfig wlan0 channel 10

and still no luck. Any ideas? again, the first 4 steps above were sufficient to get this working in Warty under Gnome. However, i really prefer KDE's look and behavior and would like to stick with it. Any ideas? If it comes to it, I might end up going back to Warty, getting everything working, then installing kde like i had done before. There are a few quirks doing it this way, but everything more or less works. 

Luckily i did have one victory, i got the fglrx drivers working in like 5 minutes (including download) for my ATI Radeon 9000 mobile. I remember what a pain that was in Suse.

---

### Post by jonny on 2005-04-10
ndiswrapper configures these cards incorrectly.  [See here](http://ubuntuforums.org/showthread.php?p=125537#post125537) for advice.

---

