---
title: "Dell Inspiron 11.10 can't connect to wireless"
date: 2011-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tornadoes28 on 2011-10-14
I have a Dell Inspiron and I upgraded to 11.10 last night and now it does not connect to wireless. Any suggestions?

---

### Post by garvinrick4 on 2011-10-14
What is your wireless card?
```
lspci -nnk | grep -iA2 net
```

---

### Post by DangeRoss on 2011-10-14
Sorry to hijack the thread, but I'm having the same problem with my Inspiron Im running the Dell 1390 card.  I'm flirting with messing around with ndiswrapper, but Im hoplessly lost.

Any help would be awesome.

-Ross

---

### Post by garvinrick4 on 2011-10-14
> Sorry to hijack the thread, but I'm having the same problem with my  Inspiron Im running the Dell 1390 card.  I'm flirting with messing  around with ndiswrapper, but Im hoplessly lost.

Any help would be awesome.Hi welcome,
 Start a thread and put the output of this in post:
```
lspci -nn | grep 0280
```and
```
lspci -nnk | grep -iA2 net
```Just to give card and driver so to get what you need to install. Hopefully will be quick for you, most are with broadcom cards I believe you have.

---

### Post by DangeRoss on 2011-10-14
Will do.  Thanks for the help.

---

### Post by tornadoes28 on 2011-10-14
Ok, now my ethernet does not even connect. Now not sure what to do since I am on Windows now so the wireless and modem works.

---

### Post by tornadoes28 on 2011-10-14
03:00.0 Ethernet Controller [0200]: Broadcom Corporation BCM 4401-BO 100Base-TX [14e4:170c] (rev02)
Subsystem: Dell Inspiron 6400 [1028:01af]
Kernel modules: b44

--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11blg WLAN [14e4:4311] (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
Kernel modules: ssb

---

### Post by garvinrick4 on 2011-10-15
> Broadcom Corporation BCM4311 802.11blg WLAN
bcm4311 is your card and below is the drivers.
Open a terminal and:
```
sudo apt-get install synaptic
```Open synaptic and type bcm in search window.
Now see the two I have marked in screenshot install those two and make sure nothing else bcm
is installed and then reboot. click on screenshot.

---

### Post by tornadoes28 on 2011-10-15
I can't install them because even with my ethernet cable connected, I still have no network connection. I need to install from the website correct? I know it's not the modem or cable because they work with Windows.

Do you know why the wired connection also does not connect to the network?

---

### Post by garvinrick4 on 2011-10-15
> Do you know why the wired connection also does not connect to the network?No I do not but you can try to restart network-manager and see if it connects. I did not know you
could not connect wired that is unusual. This will bump it up to front of Forum if restart did not help.
Or rebooting with wire plugged into router and machine. Is Cable OK? Something odd look for it.
```
sudo /etc/init.d/network-manager restart
```If cannot here can you connect wired in Live Cd (install Cd using Try Ubuntu)?
If you can let me know we will reinstall network-manager from live cd .and wireless drivers. 

Make sure in software sources you have main and multiverse open 
screenshot in next post.

---

### Post by garvinrick4 on 2011-10-15
Here is software sources. Check the two boxes and 
[code]sudo apt-get update[code]

---

### Post by marius_brkt on 2011-10-15
thks, works great, on my Inspiron 1520

---

### Post by tornadoes28 on 2011-10-15
Ok. I got wired connection. I had not installed the update Broadcom driver. 

However, after following your directions with Synaptic and rebooting, I still do not have wireless. I had wireless issues with the Broadcom driver with 11.04. Could be same issue?

---

### Post by garvinrick4 on 2011-10-15
> However, after following your directions with Synaptic and rebooting, I  still do not have wireless.  You did make sure in synaptics under search "bcm" that no other installed but the two required? 
> I had wireless issues with the Broadcom  driver with 11.04. Could be same issue

If you had an issue in 11.04 I would repeat what fixed and post here
so others may benefit.

---

### Post by garvinrick4 on 2011-10-15
```
sudo apt-get update
``` ```
sudo apt-get install firmware-bc43-installer
```
```
$ sudo apt-get remove bcmwl-kernel-source
```
```
$ sudo reboot
```

---

### Post by tornadoes28 on 2011-10-16
These are the instructions I received to fix problem in 11.04. I used option 2. But it has not fixed the problem this time. I still have no wireless.

1) installing b43-fwcutter and firmware-b43-installer as described here:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/157369](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/157369)

or

2) manually installing bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) from maverick (Ubuntu 10.10) using gdebi

Solution 2 is described here:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/23](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/23)

I suggest trying solution 2.

Then reboot your PC and run the following commands to enable your wireless adapter:

rfkill unblock all
sudo rfkill unblock all

Then retest wireless using NetworkManager.

---

### Post by garvinrick4 on 2011-10-16
Couple of new Broadcom links below:
[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

---

### Post by tornadoes28 on 2011-10-16
I tried the instructions I used with 11.04 and lost wired again. I was able to get it back before because there was a Broadcom update in the Update Manager. But now there are no updates. No wired. I am at a loss.

---

### Post by tornadoes28 on 2011-10-16
Ok. I uninstalled 11.10 and reinstalled. Followed your directions and now I have wired and wireless. Fixed. Thank you.

---

### Post by garvinrick4 on 2011-10-16
> **tornadoes28 said:**
> Ok. I uninstalled 11.04 and reinstalled. Followed your directions and now I have wired and wireless. Fixed. Thank you.
I am happy you got your internet connection back. Enjoy your Ubuntu.

---

### Post by Zauberlehrling! on 2011-12-01
I am a Ubuntu Newbie. Just installed it and already at the edge.  I have Dell Inspiron 6400 with Ubuntu 11.10 32bit and wired connection runs fine. Updated the system, but no change. Someone can help me to get it wireless?

---

### Post by notacompwiz on 2012-01-20
Help! Im having the same trouble but apparently my Dell Inspiron N4110 has an intel wireless card.  I tried the synaptic get update but the wirless is still patchy.  Any suggestions?


~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)

~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
	Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:04d7]
	Kernel driver in use: r8169

---

### Post by MickeyK on 2012-01-28
Gavinrick4, thanks a ton.  I had the same problem tornadoes28 originally described and I've got the same wireless card.  I followed your instructions and I'm good to go.  

Thanks a lot.

---

### Post by rbolan on 2012-05-03
[garvinrick4]("http://ubuntuforums.org/member.php?u=899097") Thanks a lot!!!!
   I'm a newbie here and I had the same problem; I've been searching for  while, but this thread worked just fine.

Thanks :)

---

