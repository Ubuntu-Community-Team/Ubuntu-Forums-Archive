---
title: "Dell 1545 hardware and Ubuntu 9.04?"
date: 2009-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Togezo on 2009-06-16
I recently bought a Dell 1545 laptop, which comes preloaded with Vista Home Basic. I plan to wipe the drive and replace it with Ubuntu 9.04.

I know there are, it seems, issues with dell's internal hardware, such as graphics and wireless cards, and the internal webcams. 

Essentially, if anyone could offer me advice as to what drivers to install, if any, that'd be much appreciated.

Thanks much!

Note: The dell comes with a cd for the 'webcam' software... would that work with Jaunty?

The wireless card is a Broadcom 1397 Dell WLAN card
The webcam is an integrated one, with drivers from 'Creative Technology  Ltd.'
The graphics is an ATI Mobility Radeon HD 4330
The ethernet is a 'Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller

---

### Post by lyghtkruz on 2009-06-16
I currently have an Inspiron 1520.  I loaded the Ubuntu 8.04 CD and everything worked fine on the Live CD so I installed it.  (The main things I was concerned with were Audio/Video/Wireless)  I suggest you try the same.  Download the latest (9.04 at this time) and see if everything works.

As far as the software that came with the webcam, it probably won't work on Ubuntu as it is designed for windows, but you might be able to get it to work with WINE.

-Kruz

---

### Post by superm1 on 2009-06-16
> **Togezo said:**
> I recently bought a Dell 1545 laptop, which comes preloaded with Vista Home Basic. I plan to wipe the drive and replace it with Ubuntu 9.04.

I know there are, it seems, issues with dell's internal hardware, such as graphics and wireless cards, and the internal webcams. 

Essentially, if anyone could offer me advice as to what drivers to install, if any, that'd be much appreciated.

Thanks much!

Note: The dell comes with a cd for the 'webcam' software... would that work with Jaunty?

The wireless card is a Broadcom 1397 Dell WLAN card
The webcam is an integrated one, with drivers from 'Creative Technology  Ltd.'
The graphics is an ATI Mobility Radeon HD 4330
The ethernet is a 'Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller
The currently shipping models with Ubuntu are identical except for the graphics card.  As long as you grab the latest AMD graphics driver from their website and set that up, you should be fine.

The rest of the hardware is very well supported OOTB.

---

### Post by mikewhatever on 2009-06-17
> **Togezo said:**
> ...

I know there are, it seems, issues with dell's internal hardware, such as graphics and wireless cards, and the internal webcams. 

Essentially, if anyone could offer me advice as to what drivers to install, if any, that'd be much appreciated.



You should try a live cd to see what works and what needs tuning. Dell uses a variety of parts from various vendors, which makes it impossible to answer your questions reliably. The part you posted should work out of the box without issues, except the webcam which I can't tell much about. Generally speaking, instead of paying for Vista you don't want, buy Ubuntu friendly hardware and save the trouble in the first place.

---

### Post by Mmmm on 2009-06-17
My Dell 15N notebook arrived yesterday (it has the Dell 1397 wireless card).  I upgraded it from 8.10 to 9.04. It would not connect to my hidden home wireless network (WPA and WPA2 Personal security) under either version of the OS, whether or not I used the restricted Broadcom STA wireless driver.  I changed the setting on my home network so it broadcasts the SSID instead of being hidden, and now everything works fine (with the restricted driver).

---

### Post by Togezo on 2009-06-17
Interestingly enough, I am in fact currently posting via the Firefox browser on the 'Try Ubuntu without any change to your computer' option.

Everything seems to be working fine- I literally just had to type the password and was able to access my wireless network. Ekiga seems to be able to detect my internal webcam as a video device, the graphics are working fine.

As I'm running this from the live CD, would I be correct i guessing it'll work fine once I wipe windows and install ubuntu?

---

### Post by mynameinc on 2009-06-18
Yes, my good sir, the Live CD is a representation of how well the distro will work once installed.

---

### Post by mdmadph on 2009-06-18
> **mynameinc said:**
> Yes, my good sir, the Live CD is a representation of how well the distro will work once installed.

Not to be a stick-in-the-mud, but that's not *always* the case, at least from my own experience -- I know it's weird, and doesn't make much sense, but sometimes I'll test a system with a live CD only to install Ubuntu later on to find the video not working, or the sound, or something else weird.

Any idea as to why that might be happening?

---

### Post by mynameinc on 2009-06-18
> **mdmadph said:**
> Not to be a stick-in-the-mud, but that's not *always* the case, at least from my own experience -- I know it's weird, and doesn't make much sense, but sometimes I'll test a system with a live CD only to install Ubuntu later on to find the video not working, or the sound, or something else weird.

Any idea as to why that might be happening?

Did you MD5 the file and "Check the CD for defects"?  That is very odd.

---

### Post by Cuthbeorht on 2009-06-18
> **mdmadph said:**
> Not to be a stick-in-the-mud, but that's not *always* the case, at least from my own experience -- I know it's weird, and doesn't make much sense, but sometimes I'll test a system with a live CD only to install Ubuntu later on to find the video not working, or the sound, or something else weird.
 
Any idea as to why that might be happening?
 
 
I'm not going to guess why that happens, but just put forth a word of caution. If the Live CD works well, the Full Install will work *reasonabley* well. It's not a guarantee. Like mynameinc said, check the MD5 on the CD and make sure it matches the one on the site to verify it;s a good download.
 
Once installed, start by doing updates and install any proprietary drivers you might need (ATI drivers, WiFi, etc). The System Updater and the Add/Remove Software apps usually worked fine for me on my 1545.
 
Then, you can start to troubleshoot any hardware problems. Those are the steps I've always used when instaling a new OS and they've never failed me. Let us know what happens.

---

### Post by jhahoneyk on 2009-06-19
My friend too has the same laptop with the same Broadcom wireless card. Everything else such as video/audio works fine, but the wireless card doesn't. "Hardware Drivers" app says Broadcom driver is Activated, but i can't see any wireless networks. Further, if I run iwlist scanning, it stupidly shows 'eth1' along with the normal eth0. And on all interfaces it says "doesn't support scanning". I tried deactivating the driver and activating it again, rebooting also, but didn't work.
Any idea what might be wrong?

---

### Post by superm1 on 2009-06-19
> **jhahoneyk said:**
> My friend too has the same laptop with the same Broadcom wireless card. Everything else such as video/audio works fine, but the wireless card doesn't. "Hardware Drivers" app says Broadcom driver is Activated, but i can't see any wireless networks. Further, if I run iwlist scanning, it stupidly shows 'eth1' along with the normal eth0. And on all interfaces it says "doesn't support scanning". I tried deactivating the driver and activating it again, rebooting also, but didn't work.
Any idea what might be wrong?
There is generally a switch that turns on and off wireless.  For the 1545, it's either pressing "F2" or "FN-F2" depending on what you have set in the BIOS.  Sounds like the behavior of it being in 'off' mode right now..

---

### Post by Togezo on 2009-06-19
Hello, it all went off without a hitch!

The wireles card worked fine, I just got a handy pop-up informing me about the restricted driver for the Braodcom wireless card. I had to activate and deactivate the driver a few times before it actualy connected, but it now works fine.

The only issue, currently, is that the volume cuts to 0 at around 50%, it's odd. I adjusted sound levels etc., but all it's done is make it louder, and the output decrease faster. It's still silent by the time I reach 50% volume... any ideas?

[edit: The audio is '2 Channel Intel High Definition Audio', and audio controller is an IDT 92HD71, if that helps]

---

### Post by jhahoneyk on 2009-06-19
> **superm1 said:**
> There is generally a switch that turns on and off wireless.  For the 1545, it's either pressing "F2" or "FN-F2" depending on what you have set in the BIOS.  Sounds like the behavior of it being in 'off' mode right now..

I had tried that, bluetooth works, but wlan0 isn't there. Any steps to further troubleshoot ?

---

### Post by superm1 on 2009-06-19
> **jhahoneyk said:**
> I had tried that, bluetooth works, but wlan0 isn't there. Any steps to further troubleshoot ?
The device will not be wlan0, it will be eth1 for Broadcom cards using the 'wl' driver.

---

### Post by jhahoneyk on 2009-06-20
> **superm1 said:**
> The device will not be wlan0, it will be eth1 for Broadcom cards using the 'wl' driver.

Hey thanks a lot for the help....
Now I got it, wireless networks are now shown in the NetworkManager and I can connect successfully. As for the iwlist scanning showing no results, its the same till I read the manpage and tried sudo iwlist scanning that it showed me the networks for eth1 . So, it works perfectly on ubuntu.

Now, coming to a new problem, the same laptop also has kubuntu installed on another partition, and when I use kubuntu, its not able to connect to the wireless networks (can connect to wired). It detects the networks, but when I try to connect, it says connecting for a LONG time, and then says "connecting on eth1 failed". Using a WEP password (5 digit). I manually tried to run -
```
sudo iwconfig eth1 essid "Datacentre" key s:xxxxx
```
But that didn't work either, when I check the output of iwconfig, the essid isn't getting assigned to the interface.
So,
Is this a bug in the kubuntu network manager?
If it is, how can I manually connect to the network (using the terminal) ?

Thanks a lot again :)

---

