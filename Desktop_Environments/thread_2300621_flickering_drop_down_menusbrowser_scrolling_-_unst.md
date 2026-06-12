---
title: "flickering drop down menus/browser scrolling - unstability"
date: 2015-10-27
forum: Desktop Environments
---

### Post by timber2 on 2015-10-27
Hi to all,

I am new to linux for some weeks now and I have  installed recently first lubuntu 14.04.03 and due to its misbehaviour, later lxle to an old laptop Asus L4500R Pentium M coming from windows 7 professional, with which the computer  ran very slowly but with no bugs.

Since I am very happy with  ubuntu/mint in other computer at home I thought about replacing windows 7  by lubuntu hoping for better performance. Nevertheless while running  lubuntu 14.04 from the early beginning, the computer started to have random but very frequently the issues in question (flickering drop down menus including the OS main menu/problems while browser  scrolling/for example while writing in the search boxes in the  browser, flickering, redirecting cursor to the first position, unable to  work with mouse, etc...) which led to unstability while shutdown and  reboot/start of the computer, having to restart it in safe mode.

So  I decided to install lxle 14.04 and it seemed  things got a little bit better than in lubuntu with the exception of the  flickering problem, that often makes impossible to navigate the main  OS menu with the mouse or browser scrolling without the cursor keys, and  even with them you get sometimes promptly redirected to the very start  point of the website.

I have tried combining different options in  the grub such as acpi=off and/or nomodeset and/or xforcevesa, but none  of them seem to work. With xforcevesa active things seemed to get a bit  worse.

In the propietary drivers settings, it only displays one propietary driver, which in my case is related to the modem. I  tried both options, use the driver, and the other, do not use this  device at all, with no effect to the problem in question.

As I write this post I am having the issues on and off,  and after having navigated in the ubuntu forums, I have not been able to  come across the solution. Therefore, I ask the community for help, as I would really like to run lxle/lubuntu on this computer, since these issues  tend to happen often, randomly, but not always, but when the system  works, it works beautifully.

I do not think it is about a hardware  issue, since this would have become evident on windows 7. These are my  current installation specs:

```
uname -r
3.13.0-63-generic

lspci -k
^[[5~00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS300 Host Bridge (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8107
    Kernel driver in use: agpgart-ati
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS300 AGP Bridge
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] OHCI USB Controller #1 (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8108
    Kernel driver in use: ohci-pci
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] OHCI USB Controller #2 (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8108
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] EHCI USB Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8108
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SMBus (rev 18)
    Subsystem: ASUSTeK Computer Inc. Device 8108
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] Dual Channel Bus Master PCI IDE Controller
    Subsystem: ASUSTeK Computer Inc. Device 8108
    Kernel driver in use: pata_atiixp
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] Device 434c
    Subsystem: ASUSTeK Computer Inc. Device 8108
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP150 AC'97 Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 1833
    Kernel driver in use: snd_atiixp
00:14.6 Modem: Advanced Micro Devices, Inc. [AMD/ATI] IXP AC'97 Modem (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 1836
    Kernel driver in use: snd_atiixp_modem
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS300M [Mobility Radeon 9100 IGP]
    Subsystem: ASUSTeK Computer Inc. Device 1832
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
    Subsystem: ASUSTeK Computer Inc. Device 1834
    Kernel driver in use: yenta_cardbus
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
    Subsystem: ASUSTeK Computer Inc. Device 1837
    Kernel driver in use: firewire_ohci
02:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
    Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
    Kernel driver in use: b44
02:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation WM3B2200BG Mini-PCI Card
    Kernel driver in use: ipw2200
```


During  this process of modifying grub parameters several times I noticed  another strange issue: oftentimes during authenticating for sudo gedit  the computer does not recognize the root password, having to enter it  three times before I am allowed to open the file, displaying  continuously this set of characters: ^[[5^[[5^[[5^[[5^[[5^[[5^[[5.....

Thanks in advance for any help.

---

### Post by Neil_Annett on 2015-11-24
I have almost exactly the same problem. Started off that I could restart and it would behave for a while. I tried the compiz workaround suggested on this thread: [http://ubuntuforums.org/showthread.php?t=2243912&highlight=flickering+scrolling](http://ubuntuforums.org/showthread.php?t=2243912&highlight=flickering+scrolling) . It worked for a week or so but started again and rapidly got worse. Now the Ubuntu installation on that laptop is virtually unusable and I've reverted to an old laptop which doesn't suffer this problem.

---

