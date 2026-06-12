---
title: "Dell Vostro 1000 Wireless Card Not Detected with Ubuntu 11.04"
date: 2011-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adam86md on 2011-09-02
I'm a real novice but I just installed Ubuntu 11.04 alongside Windows Vista on my ancient laptop which had slowed down to a screeching halt. Of course, Ubuntu is very simple and quick so it solved all my problems except one important one:

No wireless connection!

I click on the icon to try to view potential networks to connect to but it's not even an option. Just wired networks only. The Broadcom STA Wireless driver was automatically installed upon installation but apparently it's not cutting it. I've reinstalled several times and tried installing other drivers listed on these forums but I think my ignorance of Ubuntu and all things related to CLI holds me back from fixing it correctly.

Btw, Windows Vista still connects to my wireless network just fine as it always did.

---

### Post by mikewhatever on 2011-09-03
Your statement about the STA driver being auto-installed sounds strange. It should not do that, at least as far as I know. Please connect an ethernet cable and make sure that the bcmwl-kernel-source package (aka STA driver) is installed. If not, do install it, and if it is, try reinstalling it.
If possible, also post the output of **lspci** from a terminal window to identify your card.

---

### Post by zeii on 2011-09-24
I have the same problem / same laptop

```
Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

---

### Post by Farstanley on 2011-11-05
As it happens I installed the very same version of the very same operating system on the very same model machine for the very same reason last week.
Invoke System > Administration > Additional Drivers and follow the instructions.

---

### Post by linuxaddix on 2011-11-05
try this in terminal
lspci
so we can get a better look at your wireless card.i have a dell and always need to install the b43 firmware and fwcutter in synaptics to catch wifi.it seems its a dell wireless issue.very few distros support dell wireless cards.mine is a broadcom4311 so i use what i mentioned above.if you have the same do what i posted if not run that in terminal and post the screenshot

---

### Post by linuxaddix on 2011-11-06
> **zeii said:**
> I have the same problem / same laptop

```
Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

do as i mentioned and you both should be fine.

---

### Post by linuxaddix on 2011-11-06
you guys could try the additional driver which only comes with sta driver which is not compatible.
go to synaptic(if installed,ubuntu11.10 you have to get it from ubuntu software)
once in synaptic type in bcm
scroll down till you see firmware-b43-installer
mark it and a page should pop up stating that fwcutter will also be installed,click ok
now click on the apply tab and let it do its thing.
after installation click on the wifi icon and there you go....wifi

if bcm doesnt show up in synaptic typ this in terminal:
sudo apt-get update
enter your password and wait till its done and it should be in there
and of course you need to be with ethernet or tethering to do so.

---

