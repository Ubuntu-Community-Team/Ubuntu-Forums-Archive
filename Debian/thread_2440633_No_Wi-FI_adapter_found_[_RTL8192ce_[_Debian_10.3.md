---
title: "No Wi-FI adapter found [ RTL8192ce [ Debian 10.3"
date: 2020-04-13
forum: Debian
---

### Post by spiderparker on 2020-04-13
Hello,

I can't connect my laptop to internet via Wi-Fi.
My PCI card is an rtl8192ce and i'm running on Debian 10.3.

Here are my wireless infos : [https://pastebin.com/7MqcjcrK](https://pastebin.com/7MqcjcrK)

---

### Post by howefield on 2020-04-13
Moved to the "Debian" forum.

---

### Post by CelticWarrior on 2020-04-14
No WiFi detected. Make sure it is enabled in UEFI ("BIOS").

---

### Post by spiderparker on 2020-04-14
> **CelticWarrior said:**
> No WiFi detected. Make sure it is enabled in UEFI ("BIOS").

Network stack is enabled as well as ipv4 PXE support, ipv6 PXE support and IPSEC certificate

---

### Post by CelticWarrior on 2020-04-14
[https://wiki.debian.org/rtl819x](https://wiki.debian.org/rtl819x)

---

### Post by spiderparker on 2020-04-15
Thank you but I already modified my sources.list file as well as installing realtek firmware

---

### Post by spiderparker on 2020-04-15
I get :


rtlXXX did not boot from eeprom, check it !!


when i boot my computer

---

### Post by alexriderr on 2020-07-09
I used this command line :


"apt-get update && apt-get install firmware-realtek"



[FONT=tahoma]
[FONT=garamond][cyberflix]("https://cyberflix.info/") [aostv]("https://www.aostv.me/") [cyberflix]("https://cyberflix.cam/")[/FONT][/FONT]

---

### Post by alexriderr on 2020-07-09
[LIST]
[*]Software Requirements and Conventions Used.
[*]Scan for a Network.
[*]Generate a WPA_Supplicant Config.
[*]Set up a WPA_Supplicant Config File.
[*]Connect to Your WiFi.
[/LIST]
[VivaTV]("https://vivatv.me/")
[Beetv]("https://beetvapk.net/")

---

