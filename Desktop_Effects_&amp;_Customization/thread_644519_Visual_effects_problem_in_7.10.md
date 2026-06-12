---
title: "Visual effects problem in 7.10"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by pavankumar25386 on 2007-12-19
Hi,
i am using ubuntu 7.10(Gusty) i am not able to enable visual effect i am trying to enable it is displaying message 
**"Effect can not be enabled"**

My system config is 

RAM 256MB
C.P.U. Speed 2.88Ghz(D)

---

### Post by FuturePilot on 2007-12-19
Can you post the output of 
```
compiz --replace
```
And what is your graphics card?

---

### Post by pavankumar25386 on 2007-12-19
pavan@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by FuturePilot on 2007-12-19
What graphics card do you have?
It looks like you might have to install xserver-xgl
```
sudo apt-get install xserver-xgl
```

---

### Post by ThaRabbit on 2007-12-19
> **FuturePilot said:**
> What graphics card do you have?
It looks like you might have to install xserver-xgl
```
sudo apt-get install xserver-xgl
```

He should be fine without Xgl, Xorg should be fine... the problem, I think, lies in the lack of a whitelisted driver.

Same question:
What videocard are you using and have you installed any specific driver?

System -> Administration -> Restriced Driver Management

Does that offer any specialised drivers for your videocard?

---

### Post by pavankumar25386 on 2007-12-20
how can i know my Graphics card.....??/
how to install its drivers??

---

### Post by erfahren on 2007-12-20
> **pavankumar25386 said:**
> how can i know my Graphics card.....??/
how to install its drivers??
go to the terminal (Apps > Accessories) and enter this:
```

lspci

```
look for the "VGA compatible controller:" line. and post it here.

You can install the restricted proprietary driver by going to System > Administration > Restricted Drivers Manager (it may not be enabled by default).

--- oh, before you do that go to System > Administration > Software Sources and make sure they are all enabled (except "Source code). - then enable the driver and reboot.

If you have an ATI card you will need to install "xserver-xgl" as mentioned. you may have to restart X (the X Window System) before you try enabling the desktop effects (press Ctrl+Alt+Backspace to restart X)

---

### Post by mdau2508 on 2007-12-20
go to system appearance and under visual effects uncheck extra

---

### Post by pavankumar25386 on 2007-12-20
Output of  **lspci** is 

[B]pavan@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
pavan@ubuntu:~$ 

[/B]

Wat i have to do next ??

---

### Post by NateMan on 2007-12-20
[http://ubuntuforums.org/showthread.php?t=485646&highlight=compiz+unichrome](http://ubuntuforums.org/showthread.php?t=485646&highlight=compiz+unichrome)
check out that thread.

---

