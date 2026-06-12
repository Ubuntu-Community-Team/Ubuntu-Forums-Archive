---
title: "Cannot make Wireless connection work on D610"
date: 2009-02-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arepaking on 2009-02-23
Hello,
I've been following a lot of steps out there for the D610 but none of them helped me to make my wireless connection work. At this point I don't know if I messed up my system by following several solutions.

I was wondering if someone could help me from scratch to try to solve my problem?

Thanks in advance,
AK

---

### Post by arepaking on 2009-02-23
These are the output from:

IWCONFIG:
```
user@user-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```



LSCPI:
```
03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
```

---

### Post by Mordac85 on 2009-02-24
Not sure where I got these from (props to the author), but they've always worked on my older Latitude systems.
```
Setup Dell 1390 WWLAN:
1. Clean the system
	sudo rmmod ndiswrapper
	sudo ndiswrapper -e bcmwl5
	sudo apt-get remove ndiswrapper-utils
2. Update system
	sudo apt-get update
	sudo apt-get install build-essential
	sudo apt-get install linux-headers-`uname -r`
3. Get the packages
	ndiswrapper
		wget [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)
	Dell drivers
		wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
4. Unpack it
	tar -xzvf ndiswrapper-1.47.tar.gz
	unzip -a -d YOUR-DRIVER-DIRECTORY R151517.EXE
5. Blacklist the old driver
	sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
	if permission is denied:
		sudo -s
		echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
		exit
6. Reboot
7. Compile ndiswrapper
	cd YOUR-NDISWRAPPER-DIRECTORY
	sudo make uninstall
	Note: Repeat above until there are no more files/dirs removed
	sudo make
	sudo make install
8. Install the drivers
	cd YOUR-DRIVER-DIRECTORY
	sudo ndiswrapper -e bcmwl5
	sudo ndiswrapper -i bcmwl5.inf
	sudo ndiswrapper -l
 	Note: You should see a message that says driver present, hardware detected
	sudo ndiswrapper -m
	sudo modprobe ndiswrapper
	sudo echo ndiswrapper >> /etc/modules
	if permission is denied:
		sudo -s
		echo ndiswrapper >> /etc/modules
		exit
	WiFi LED should now be lit!
9. Reboot (not required but a verification)
10. Test it
	sudo iwlist scanning
```

---

