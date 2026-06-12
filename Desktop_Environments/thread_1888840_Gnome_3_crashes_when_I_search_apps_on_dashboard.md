---
title: "Gnome 3 crashes when I search apps on dashboard"
date: 2011-11-30
forum: Desktop Environments
---

### Post by mr.ioso on 2011-11-30
Hello. I am new to this forum but I think someone can help me.

When I use the dashboard to search for applications or drag apps in the bar showing the favourites gnome-shell crashes.

Any idea how to fix that? Or just wait for an update?

Thank you.

---

### Post by Frogs Hair on 2011-11-30
Hello and Welcome

This is not normal behavior and I would start by providing some information about your computer . To get information about the graphics card / chip run the following command in the terminal . ```
lspci
```
Copy and paste the information here in code tags using  the # symbol on the top of reply box .

---

### Post by mr.ioso on 2011-11-30
Hello. Thank you for your answer. Yes it is really weird an I cannot stop typing to see if it works :D

Here the output of lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

---

### Post by Frogs Hair on 2011-11-30
The make and model of the computer would be helpful too .

---

### Post by mr.ioso on 2011-11-30
Ok, sorry for that. As I said, I am new to the formum :confused:

It is a Dell Vostro 3500 running Linux Mint 12 (Lisa). When I am switching to Unity 2D everything works fine, also the dash search. Gnome 3 causes gnome-shell to restart, so all control elements disappear and restart after a few seconds.

---

### Post by Frogs Hair on 2011-11-30
Have you checked in additional drivers for any proprietary drivers for the graphics card / chip ? I'm thinking the graphics card may be struggling a bit with Gnome . From what I found your computer has no compatibility problems with Ubuntu , but information about the Gnome Shell is hard to find because it is not the default desktop . If you can run Unity 3D you should have no problem with the gnome shell , but as you wrote you use 2D .

---

### Post by mr.ioso on 2011-12-01
Jockey-gtk does not show any other drivers. I am using the xserver intel driver on my machine.
I installed Unity-2D as additional window manager to see if it works.

Well If I do not use the search or drag and drop items within th dash, everything works.. Strange..

Does anyone know if it helps changing the code in the *.js files located in
```
/usr/share/gnome-shell/js/ui/
```
?

---

### Post by Frogs Hair on 2011-12-01
You can see if it is theme related by changing the shell theme . Checking Looking Glass for errors may indicate something helpful . If you don't how to use Looking Glass see the link . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by mr.ioso on 2011-12-01
Okay, it is not theme related. I checked a few different themes but it still crashes

---

### Post by Frogs Hair on 2011-12-01
The only information I have found for graphics requirements indicates that a 3D card or chip is required for the shell . There is no list of hardware available and the shell is supposed to run on low end 3D hardware .

---

### Post by vanlong441 on 2011-12-04
gnome shell does crash sometimes when typing in dash too fast and using multiple workspaces. The only solution I've found so far is to upgrade gnome-shell to the latest version. Mine is 3.2.1 at the moment.

---

### Post by MARP1961 on 2011-12-06
Strangely enough, I encountered this problem for the first time today. Whenever I went to Overview Screen and started to type (to do an Application Search), the shell would simply freeze. The laptop then required a forced shutdown.

On trying to think of something I'd changed, I remembered selecting a different Shell Theme (Adwaita White Netbook) earlier. I decided to revert back to the Gnome Shell default and the problem has now gone. I am now going to see if the problem resurfaces with other Shell Themes.

---

### Post by MARP1961 on 2011-12-06
Yes, I have the same problem again if I select 'Atolm' theme. No problem on reverting to default.

---

### Post by mkhc on 2012-01-04
I'm having this problem too and it doesn't seem to make any difference which theme I'm in. Unity works as does gnome "classic" but not gnome's main shell search.

This is only happening on my main computer - my laptop seems fine with it.

My gfx card is " ATI Technologies Inc RV280 [Radeon 9200 SE]"

---

### Post by linfidel on 2012-01-06
FWIW, I have this problem consistently, with or without proprietary drivers.  I have an AMD motherboard, with an Asus AMD 5450 (ATI Radeon) card.  Never had any problems before, and the Unity shell works fine.

Not only that, but messing around with Gnome3 settings has left the system unbootable twice now.  It might have been either from trying to use the alternate driver, then disabling it while experimenting.  Trying to use Gnome 3 with the standard proprietary driver has a lot of corruption in the Gnome shell text, which is fixed temporarily by resizing the fonts.

Needless to say, I'm beginning to like Unity more and more.

---

