---
title: "Wi-Fi WLAN problems"
date: 2006-08-12
forum: Desktop Environments
---

### Post by alwbsok on 2006-08-12
I originally bought a wireless router from Belkin. It worked fine with Ubuntu. Unfortunately, it started to turn itself off, so I had to replace it with a shiny new Billion 7401VGP.

I set all the settings on the Billion so that the computers on the network wouldn't need to change any settings. I made the ESSID the same, the channel the same, the key and encryption the same, and the IP address of the device the same. On my XP partition, this worked: I didn't need to change a thing, but Ubuntu continues to report that the card (eth1) is disconnected.

I've tried to fiddle with the settings on Ubuntu, but nothing seems to work. I checked the network tool (without knowing how to use it), and it reported that packets were being sent and recieved, but the counters reset constantly. When I tried removing the encryption, the counters didn't reset, but the card didn't connect. The system does work via ethernet (eth0) and on Windows, so the router seems to be working. I am happy to provide any details that you need.

Can you help me? Thanks in advance.

---

### Post by maniacmusician on 2006-08-12
where does ubuntu say that the card is disconnected?

in terminal, type iwconfig and post the results.

---

### Post by alwbsok on 2006-08-12
This is what iwconfig said:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"belkin54g"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Thanks for answering, by the way.

---

### Post by alwbsok on 2006-08-13
I really need help! I don't care who you are, but if you can help, it would be greatly appreciated.

---

### Post by lupine_nickt on 2006-08-13
Ubuntu isn't finding the access point for some reason.

Can you post the contents of /etc/network/interfaces and the output of 'iwlist eth1 scan' ?

Most likely, all you need to do is to order it to associate to the AP - this is done by issuing the command 'iwconfig eth1 ap <mac address>'

iwlist eth1 scan gives you the MAC address (called "Address" - it's a set of hex numbers, seperated by colons (e.g. 00:0F:EA:F0:E4:F3)

HTH

xF,

...Nick

---

### Post by alwbsok on 2006-08-13
Thanks for replying. Sorry I didn't reply earlier, but internet access is a little difficult right now.

I tried your suggestion of changing the access point. It still doesn't seem to work.

Here are the contents of /etc/network/interfaces

--begin--

auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp





iface eth1 inet dhcp
wireless-essid belkin54g
wireless-key 25121987251219872512198725

auto eth1

--end--

Here is the results of $iwlist eth scan

--begin--
eth1      Scan completed :
          Cell 01 - Address: 00:30:65:20:52:FF
                    ESSID:"ocean terrace"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=73/100  Signal level=-55 dBm
                    Extra: Last beacon: 24ms ago
          Cell 02 - Address: 00:0F:B5:B9:0E:1A
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=77/100  Signal level=-52 dBm
                    Extra: Last beacon: 228ms ago
          Cell 03 - Address: 00:13:D3:6E:92:99
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=72/100  Signal level=-27 dBm
                    Extra: Last beacon: 64ms ago

--End--

Thanks again.

I also noticed after the $iwlist command that the MAC address for Cell 03 differs from the address that I entered in through $iwconfig (I got it from the router's interface, in the "Address" field). I've tried both and neither worked.

---

### Post by maniacmusician on 2006-08-13
have you tried just configuring it through the Networking GUI? I'm not sure where that is in Gnome, it's in the menus. and it seems that your essid is supposed to be "belkin54g" from what /etc/network/interfaces says. The GUI utility usually does it for me.

---

### Post by encompass on 2006-08-13
additionally, I would jsut see if you can get a connection at all... take down the encription and see if it works... then go from there... and in gnome it is the program called network-admin from the console.
You can setup things there.
Looks like your card, so far, works very well, you are able to see everyone's wireless connections.  You can set it up.
But, I think you could check the most basic of setups.
Bummer about the news.

---

### Post by alwbsok on 2006-08-13
Believe me, I've tried the GUI setup. It doesn't seem to be working. I've also tried taking down the encryption, but I'll try it again and see if it works.

---

### Post by encompass on 2006-08-13
you could have missed typing something... for the longest time I had the caps wrong.  I know you setup worked last time... but you never know.  Additionaly, it could be the routers fault.  If it is a different computer it may not allow you to connect because it mac filters or other what not.  Wireless is one of the most difficult things to work with.  Graphics cards are number 2.:sad:

---

### Post by alwbsok on 2006-08-13
I've tried it. It still doesn't work. I tried iwconfig, and it again reported "Access Point: Not Associated". I've changed it again to the MAC address the router tells me it is.

---

### Post by alwbsok on 2006-08-13
I've typed and retyped all the fields (I know the dangers of capslock). My connection is unencrypted. A friend of mine is running Ubuntu 6.06 with the same model router (he recommended it to me). I don't understand it.

Thanks for helping all the same.

---

### Post by djSeverin on 2006-08-14
From reading this, it seems you have tried just about everything. My addition would be check the country AND channel that you are trying to use. Also, try setting ESSID to auto, let the card detect this information itself and see if you can get ANY connection, to ANY network.

Have you checked to make sure the router's firmware is up to date? And the firmware is for the right country? I'm in Aus and discovered that for my Billion router, there was firmware JUST for Australia, though this was not made clear on their international site.

---

### Post by valorin on 2006-08-14
I am having the same problem. My hardware is completely different, tho.

I have an AirPort Express Base Station and a Netgear WG511 wireless PC Card. They have worked flawlessly in the past, however, after a standard Ubuntu update the PC Card simply refuses to connect in Linux. I've checked everything mentioned in this thread, and I know my settings are right cos they were working and I did not changed then.

Therefore, I can only assume that something was screwed up in the latest update which is affecting our wireless cards.

---

### Post by alwbsok on 2006-08-14
I've changed the channel to 11, I've set the essid to any, I've flashed the firmware. I don't know how to set the country. I'll try to connect to my friend's router (same model as mine, on same distro, except his works).
I'll post again tomorrow sometime. Thanks for helping.

---

