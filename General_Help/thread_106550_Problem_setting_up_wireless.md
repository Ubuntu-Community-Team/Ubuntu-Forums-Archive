---
title: "Problem setting up wireless"
date: 2005-12-20
forum: General Help
---

### Post by zanglang on 2005-12-20
Hi, I'm having some odd problems with setting up my wifi connection on my laptop (DWL-G650+ on Compaq 1721), would really appreciate some tips on fixing it!

I seem to be able to connect to the router fine, iwlist scan and iwconfig confirms my settings were correct, and while bringing up wifi with ifup wlan0 shows dhclient obtaining the IP correctly... but when i type ping google.com, it simply says "Unknown host google.com"?

I'm not sure if it's the router's DHCP problem, because when booting into Windows XP it seems to work perfectly.

Another odd issue i'm having is that wifi-radar only seems to scan lo, sit0 and eth0, while skipping wlan0 entirely? (Checked using 'wifi-radar -d')

Help, please? Thanks in advance!

---

### Post by kb3hkg on 2005-12-20
sounds like wifi radar might be your problem, by default that D-Link card is ath0 unless you changed this. Check to see if using this might help. I have the card and it has worked flawlessly in Ubuntu.

---

### Post by kingsidy on 2005-12-21
just a little suggestion i think that gtkwifi manages the wireless access points better than wifi radar. Wifi radar acts funny sometimes.

---

### Post by zanglang on 2005-12-21
Hmm, nope, I think wlan0 was default when I first plugged in the card. While doing some quick research I read only Atheros chipset cards like G650 (without the '+'!) use ath0, and my G650+ uses ACX111?

Oh, by the way, my Badger's firmware has already been upgraded using the wiki's instructions:
[https://wiki.ubuntu.com/DWLG650WiFi?highlight=%28g650%29](https://wiki.ubuntu.com/DWLG650WiFi?highlight=%28g650%29)

kingsidy:
Thanks for the suggestion, will try it out as soon as i iron out this problem first and get online. ;)

---

