---
title: "Dell Mini 10v compatibility"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TriBlox6432 on 2010-05-02
Just wanted to let those of you know who have a mini 10v (or mini 9) that **everything **except wireless works out of the box.  

To get wireless working you just need to plug it into Ethernet, click System>Administration>Hardware Drivers, install the Broadcom STA wireless driver, and reboot.  Works flawlessly.  Way to go Ubuntu!

---

### Post by sb5551 on 2010-05-04
This is true everything is working out of the box except the wireless.
 
I followed what you said TriBlox and my dell can see the wireless networks but can't ever connect. I keep getting messages to re input my password every couple of minutes and it keeps flashing disconnected then connected, but I can never get a webpage to open.

---

### Post by Matt__ on 2010-05-05
I cant get my 10v to connect wirelessly.
I applied the b43** driver when i was installing and it connected, subsequent update and/or the reboot disabled this so I uninstalled the driver and tried the STA variant. this failed several times and locked my system up, now I dont even have an option for wireless via the icon on the top panel.
I also no longer get the option for the b43** driver.
I would love 10.04 were it not for this.

jocky log repoerts this...
```
2010-05-05 15:05:11,838 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-05 15:05:12,106 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-05 15:05:12,367 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-05-05 15:09:06,501 DEBUG: Shutting down
```

#considers downgrade to 9.04 which worked perfectly

---

### Post by sb5551 on 2010-05-05
Is this considered a bug then?

---

### Post by Matt__ on 2010-05-05
Still no wireless for me.
Ive followed threads on wicd, installing source for the b43 drivers/STA, installed ndis wrapper, reinstalled all of 10.04 and all for nothing :P

using 9.04 from a USB stick at the moment as a netbook without wireless is like a car without wheels!

anyone got suggestions as to what i try next ?

---

### Post by sb5551 on 2010-05-05
I still havent figured it out yet either. I am contemplating going to 9.10, but I dont want to have to buy another usb drive to burn it on to. My 10v only came with a cd with 8.04 on it, and I just used my last usb drive to put 10.04 on the netbook. Doh!!

---

### Post by 2nubu on 2010-05-10
Hello, 

How well does Lucid Lynx work with Dell Mini 10v, after upgrading from Hardy Heron?

Also, if I have an Intel Atom N 270 chip and 1GB RAM, is that good enough to support Lucid Lynx?

Thanks,
2nubu

[Sorry, I'm new here (hence the screen name :) ). Still trying to figure these forums out.]

---

### Post by Groodles on 2010-05-12
A question to the people having problems with Mini10v Wireless:

Did you install 10.04 from the release CD/DVD or upgrade from 9.10?

(I originally installed 9.04, upgraded to 9.10 and then upgraded again to 10.04.  Everything on my Mini10v worked **WITHOUT** having to update via the Wired ethernet connection.  I'm guessing that I installed the Broadcom driver waaaay back at 9.04 and it's kept it/updated it as I've done distro-upgrades.)

---

### Post by awlinux on 2010-05-12
Hi

Have 10.04 (UNR) running fine, new install everything works well, Wireless working fine using the wired method using the Broadcom STA driver.

Used wireless process from Ubuntu Mini site [here]("http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html") to install.

---

