---
title: "Problems with steam [64 bit]"
date: 2013-04-22
forum: Gaming &amp; Leisure
---

### Post by piedog98 on 2013-04-22
Hi all, a large problem here. 

I just switch to ubuntu after learning c and fed up with windows 8 (stupid OS). I have installing steam, but when i click on it it, the icon just flashes and nothing happen. i have tried apply patch, STEAM_RUNTIME=0  and a clean uninstall/install. i really want play css and i would appreciat e help swift.

---

### Post by QIII on 2013-04-22
*Moved to **Gaming and Leisure***

---

### Post by oldrocker99 on 2013-04-22
Open a terminal, and try typing
steam

and post the results.

---

### Post by piedog98 on 2013-04-23
[][][][][]@[][][][][]-M14xR1:~$ steam
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1366403468_client)
Xlib:  extension "GLX" missing on display ":0.0".
Installing breakpad exception handler for appid(steam)/version(1366403468_client)
Installing breakpad exception handler for appid(steam)/version(1366403468_client)
unlinked 0 orphaned pipes
Xlib:  extension "GLX" missing on display ":0.0".
OpenGL GLX extension not supported by display[][][][][]@[][][][][]-M14xR1:~$

result of steam in shell.

---

### Post by whatthefunk on 2013-04-23
What video card do you have?  What video driver do you use?  Post the output of these two commands:
```
lspci
```
```
jockey-text -l
```

---

### Post by piedog98 on 2013-04-23
lspci output:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev a1)
07:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

jockey-text -l output:

()

nothing happened on the jockey-text output -l

---

### Post by whatthefunk on 2013-04-23
Find _Additional Drivers_ and open that up.  It should tell you what video driver youre using.  My guess is that the driver is the root of your problem.

---

### Post by piedog98 on 2013-04-23
"no propietary drivers are in use on this system" what this does mean and what i do about it

---

### Post by Bölvaður on 2013-04-23
> **piedog98 said:**
> "no propietary drivers are in use on this system" what this does mean and what i do about it
This means that there are no proprietary drivers installed. Most commonly those are drivers provided by ATI or NVIDIA.
As you have GeForce GT 555M you should have seen some NVIDIA driver pop up in Jockey (aka. Additional Drivers)

> **whatthefunk said:**
> Find _Additional Drivers_ and open that up.

Do you see any drivers in here? If so, click the driver and press "activate".
I suggest activating the latest drivers which you will be able to choose from.


This is the best way to install drivers for people that aren't used to Linux and don't want to change something so they don't know what to do about it except reinstall. I install beta NVIDIA drivers from their website, which I recommend only if you want to read on how to do it (very unintuitive), consider risk screwing something up as not a problem, and want to learn how to do this.

---

### Post by whatthefunk on 2013-04-23
It means that you are using the open source drivers.  In the Additional Drivers window, are there other drivers listed?  I would try nvidia-current

---

### Post by piedog98 on 2013-04-23
i have play 3d games before, i have install NVIDIA GT550m. when i have windows i could play counter strike source, planteside 2, dead island, halo, battlefield 3, just fine.

---

### Post by piedog98 on 2013-04-23
there is only empty list in additional driver window

---

### Post by myromance123 on 2013-04-23
Your graphics card is an Nvidia GT555M
> 01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev a1)
But you also have an Intel Integrated graphics card
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

My honest guess is that you're using a laptop/notebook or some form of mobile device yes?
To install the graphics drivers for your system, we're going to use something called BumbleBee. This software will help install the Nvidia driver for your system. Just follow my instructions as below.

Open a new Terminal, and type in the following lines one-by-one. If it asks for your password, type it in and hit Enter.
```
sudo add-apt-repository ppa:bumblebee/stable
```
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update
```
```
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```
Now, simply restart your computer and hopefully you should be up and running with your Nvidia drivers on start up.

P.S: The source for the commands I'm giving are taken from here:[ LINK]("https://wiki.ubuntu.com/Bumblebee")

---

### Post by whatthefunk on 2013-04-23
> **Bölvaður said:**
> This means that there are no proprietary drivers installed. Most commonly those are drivers provided by ATI or NVIDIA.
But as you have Intel GPU then we are playing a different set or rules, as Intel provides open source drivers (which is good).

????????????

His lspci output:
> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
 00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
 00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
 **01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev a1)**
 07:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
 0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
 13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
 13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
 19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

---

### Post by piedog98 on 2013-04-23
&#1077;&#1073;&#1072;&#1090;&#1100; &#1076;&#1072;! works well now, thank you for bumblebee mister

---

### Post by matt_symes on 2013-04-23
Hi

Just a note. 

Depending on the version installed, jockey was removed as it caused problems when installing graphics drivers on certain PCs

Kind regards

---

### Post by myromance123 on 2013-04-23
> &#1077;&#1073;&#1072;&#1090;&#1100; &#1076;&#1072;! works well now, thank you for bumblebee mister 
Glad you got it working, happy gaming :)

---

### Post by Bölvaður on 2013-04-23
yeah, didn't notice.
Fixed my reply accordingly, but bumblebee is the way to go as mentioned above.

---

