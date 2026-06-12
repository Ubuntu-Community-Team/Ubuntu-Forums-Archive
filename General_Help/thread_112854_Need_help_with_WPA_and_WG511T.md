---
title: "Need help with WPA and WG511T"
date: 2006-01-05
forum: General Help
---

### Post by linb0x on 2006-01-05
Hello all. I have recently (about 3 months) jumped on the linux ship with Ubuntu 5.10.

I love it. At first I was dual booting, but recently built a dedicated box.

So I decided I want to dual boot my laptop. Got everything up and running smoothly. 

Internet works fine when I drop all the security on my WAP.

Problems start when I try and set up WPA. I followed the faq here: 

[https://wiki.ubuntu.com//WPAHowto](https://wiki.ubuntu.com//WPAHowto)

I can't for the life of me get it to work. I followed it to the letter. Here are what my files look like:

_**wpa-supplicant.conf**_

network={
              ssid="h4xn3twifi"
              proto=WPA
              key_mgmt=WPA-PSK
              psk=......................
}

**_wpasupplicant_**

ENABLED=1

OPTIONS="-iath0 -c/etc/wpa_supplicant.conf -Dmadwifi"

**_interfaces_**

auto ath0
iface ath0 inet static
wireless-essid h4xn3twifi
address ***.***.*.***
netmask ***.***.***.***
gateway ***.***.*.***

pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5

When I run the following from the faq:

wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi

I get:

siocsiwpmksa operation not supported

And an endless loop of unsuccessful attempts to connect the wifi. Some list the correct MAC, some are all 0's.

Can anyone PLEASE help me here. I stayed up all night working on this for 8 hours and I am lost. I wish 5.10 would have had WPA right out of the box.

Thanks.

---

### Post by linb0x on 2006-01-05
Can anyone please assist?

This is driving me batty!

---

### Post by linb0x on 2006-01-06
Anyone ?

---

### Post by spier on 2006-01-06
Well, I'm a very beginner, but, as far as I can tell, these wpa things are hard related to the hardware (no pum intended). I got wpa working in my centrino (with ipw2200 driver)  following this howto, slightly different (and more complex) than yours:
[http://www.ubuntuforums.org/showthread.php?t=26623]("http://www.ubuntuforums.org/showthread.php?t=26623")

Good luck!

---

