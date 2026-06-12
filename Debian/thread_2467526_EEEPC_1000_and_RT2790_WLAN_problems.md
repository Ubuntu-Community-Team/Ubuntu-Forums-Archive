---
title: "EEEPC 1000 and RT2790 WLAN problems"
date: 2021-09-29
forum: Debian
---

### Post by fierce on 2021-09-29
Hi all

I have a very old EEE PC 1000 and I am trying to get life out of it by installing Debian onto it.  I have not tried Ubuntu yet but I'm at my wits end with this thing, and if using Ubuntu means I'll get support then I'll happily try it!

I am a novice user though, and unsure what is wrong with the wireless card.

Originally, when I installed Debian, I could not get the wireless device to to even turn on at all, there is an indicator light on the front of the netbook.  FN+F2 to physically turn the WLAN switch on the device would only make the light turn on for a second, then immediately turn back off.  'lspci' would show no wlan related results, at all.

'rfkill list' would show that eeepc-wlan was Soft Blocked but not Hard Blocked.  'rfkill unblock all' would do the same thing as FN+F2 - just trigger the light on for a second, then immediately shut off.

I came across this old thread while trying to research the problem: [https://ubuntuforums.org/archive/index.php/t-1587107.html](https://ubuntuforums.org/archive/index.php/t-1587107.html)

which lead me to add these lines to my /etc/modprobe.d/blacklist.conf

```

blacklist rt2xxpci
blacklist rt2800pci

```

and add these lines to /etc/modules

```

rt2860sta
rt2860

```

And now, upon reboot, I finally have the wireless light staying on!  And lspci displaying the wireless card.  And 'rfkill list' displays SOFT BLOCKED & HARD BLOCKED both as NO.

[http://ix.io/3Als](http://ix.io/3Als) is my dmesg output
[http://ix.io/3Alu](http://ix.io/3Alu) is my lspci output

But now I am fully stuck, and unsure how to proceed.

None of the wireless utilities I've tried show any wireless devices.  'ip link show' only displays lo and enp4s0 which is my ethernet.

Any next steps, help, or suggestions would be greatly appreciated!

Thanks very kindly

---

### Post by fierce on 2021-09-29
also, is there any way to tag a user to alert him to a thread?  there is a particular poster I've seen on many previous helpful UbuntuForums thread named "chili555" and I feel like he's the guy to help me

---

### Post by ajgreeny on 2021-09-29
Show us the output of terminal command ```
inxi -n 
``` which will show us information about your network hardware and may give us more clues.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by fierce on 2021-09-29
Absolutely!  I had to apt-get install inxi as it did not exist on my system:

```

Network:   Device-1: Ralink RT2790 Wireless 802.11n 1T/2R PCIe driver: N/A 
           Device-2: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet driver: ATL1E 
           IF: enp4s0 state: down mac: 00:22:15:8e:a2:78 
           IF-ID-1: usb0 state: unknown speed: N/A duplex: N/A mac: 2e:ed:dd:f4:b3:10 

```

---

### Post by mikewhatever on 2021-09-29
AFAIK, Debian does not include proprietary wireless firmware, almost all wireless cards need. For whatever reason, they call it "some obscure wireless cards". Pretty sure their wiki has more info.

---

### Post by guiverc on 2021-09-29
I can't really help (*I hate wireless; only using it when I need to - but given I largely use desktop machines that's not common*).

I will say I used an

```
asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
```

in QA-testing Lubuntu, Xubuntu & other *flavors* of Ubuntu up to and including into the *disco* or 19.04 cycle (*it was i386 only; or 32-bit, so my using it ended when i386 ISOs disappeared*). 

It was last used probably [Aug-2020 in QA-testing 18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") though I don't recall how extensively (a last RC test can be found [here]("http://iso.qa.ubuntu.com/qatracker/milestones/415/builds/218707/testcases/1303/results") but you'll note it wasn't an extensive test; as prior testing would have shown issues & that test was quick before I switched to installs which are the issue close to release; there maybe others for other *flavors* too if you look).

I used that device in QA-testing Debian too (*non-free* ISOs in most cases; some boxes I know have issues when *default* Debian ISOs are used, so I test some regular QA-test boxes using those *official* ISOs before quickly shifting to the *non-free* ISOs that work on all devices when testing Debian/Ubuntu).  FYI:  Ubuntu using *free only* have the same issues as Debian; the difference is *non-free* is default for Ubuntu; but on a different ISO for Debian.

I didn't need to do anything on my eeepc on any release (Debian 7-11) that I recall.  Mine has Debian installed on it, but I don't see release details in your question (*sorry if I missed them*).

---

### Post by arochester on 2021-10-05
You need to install the package firmware-ralink. 

[https://wiki.debian.org/rt2800pci](https://wiki.debian.org/rt2800pci)
Note! Its no longer Debian 8 "Jessie" or deb [http://httpredir.debian.org/debian/](http://httpredir.debian.org/debian/) jessie main contrib non-free - the latest stable issue is Debian 11 "Bullseye"

[https://wiki.debian.org/WiFi](https://wiki.debian.org/WiFi)

---

### Post by jeremy31 on 2021-10-05
I would undo the changes to the blacklist and /etc/modules and reboot, then see the wireless script link in my signature and post results.  The firmware is part of Ubuntu linux-firmware package

---

