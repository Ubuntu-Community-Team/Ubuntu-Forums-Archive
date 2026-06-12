---
title: "need help with my acer"
date: 2009-02-07
forum: General Help
---

### Post by wtigerks on 2009-02-07
i have acer aspire one and it has 3g and i need help seting it up i have att for my wireless i hope someone can help thanks .o and i am on eeubuntu ubuntu 8.10 thanks .:p

---

### Post by avtolle on 2009-02-07
Which wireless card do you have? From the terminal ```
lspci
```and post results.

---

### Post by wtigerks on 2009-02-09
dalesacer@dalesacer-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
dalesacer@dalesacer-laptop:~$

---

### Post by wtigerks on 2009-02-09
some where there is a 3g i don't know the name of it so i am new at this and i am learning thx .

---

### Post by Ketara on 2009-02-09
**03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**

is your wireless card. I'm not entirely sure what you mean by 3G, are you talking a USB AT&T thing?

Atheros cards can be kind of a pain, but you should be able to get that working through this thread - [http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros+5007](http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros+5007)

Although as a disclaimer, I couldn't get mine working through the above, and had to use ndiswrapper.

---

### Post by kevh on 2009-02-09
I have been running (and stopping) Ubuntu on an Aspire One since December and would suggest you follow the documentation here...[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
Read it slowly and double read the **Note**s.. For example "Kernel 2.6.27-11 breaks the wired ethernet interface" I lost hours on that one and the only solution seems to be to not yet upgrade and keep checking the bug status. A couple of other threads / howto's that I have found particularly useful have been...
For multimedia... [http://ubuntuforums.org/showthread.php?t=766683&highlight=install+skype](http://ubuntuforums.org/showthread.php?t=766683&highlight=install+skype)
For sound / pulseaudio I found this really useful....[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I also found this helpful in getting my surround sound working...[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
Have fun!!!
Kev

---

