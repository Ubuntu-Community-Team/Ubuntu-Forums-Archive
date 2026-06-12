---
title: "ubuntu 7.10 freezing often!"
date: 2008-01-15
forum: Desktop Environments
---

### Post by rlwilson2 on 2008-01-15
I am new to Ubuntu (3 days) I installed 7.10 on a new 360 gig HD on a P4 3.0 Gig 775 System with a ECS board and on board vid and 1 gig of DDR2.  

I like the system however I am experiencing a lot of system resets due to the OS? freezing.  It is random although 90% of the time I have the web browser open. However sometimes with the browser closed it will do it also.  the screen freezes no mouse movement or keyboard response.  I have walked away from it and came back 10 min later to it working again however I have waited 15 Min on it and no response still.  I switched from firefox to epiphany web browser and the freezing has been significantly less however I am having to restart the system every 45 min or so ( approx not exactly 45 min apart) 

Is this normal?  I would hope not. 

Please help I am intrigued by the Ubuntu and want the system to work I just am unfamiliar with it and its settings.  

Please explain what you need from me to help diagnose and how to do it an I will be glad to comply.

Thank You for you help.

---

### Post by Sef on 2008-01-15
> Is this normal? I would hope not.

Please help I am intrigued by the Ubuntu and want the system to work I just am unfamiliar with it and its settings.

Please explain what you need from me to help diagnose and how to do it an I will be glad to comply.


1) Run the Live CD for a few hours and see if this happens.

2) If it doesn't happen with the Live CD, then likely you have a bad install, and I would reinstall.

3) If it does happen, then either you have a bad Live CD, or there is a hardware problem.

4) Post how the Live CD run goes, then I'll offer more ideas of what to do.

---

### Post by rlwilson2 on 2008-01-16
Thanks for the help!  Great Idea....

I have found out a few things: a. the system is stalling or busy or...  I don't know the term... if I wait it will come back fine random occurance random amout of time needed for it to recover..  I still do not think that this is normal.. 2.  it happens when running on the live CD not as often but it still is happening..  What Next... Thanks

---

### Post by rlwilson2 on 2008-01-17
Bump.....   I realy need help with this.....

---

### Post by TheLions on 2008-01-17
try run a memory check maybe fou have corrupted RAM

---

### Post by rlwilson2 on 2008-01-17
> ry run a memory check maybe fou have corrupted RAM 

How do I do this?  Thanks

---

### Post by rlwilson2 on 2008-01-17
Ran Memory Check on the Ubuntu disk no failures  What next???

---

### Post by PierGroup on 2008-01-17
Is the hard_drive_active light flashing frequently during these freezes? Also, is your hard drive a SATA one?

---

### Post by rlwilson2 on 2008-01-17
> Is the hard_drive_active light flashing frequently during these freezes? Also, is your hard drive a SATA one? 

Drive is not busy light off/ Dive is EIDE

---

### Post by Mithrilhall on 2008-01-17
Could you issue this command on the console and post the results:

```

lspci

```

Also, try running the Sidux live CD and see if you have the same problems.

---

### Post by danyf on 2008-01-17
Try adding "acpi=off irqpoll" to the kernel boot options (in /boot/grub/menu.lst). This solved a similar problem I had.

By the way, does anyone know how to keep additional kernel options when upgrading the kernel with apt-get?

---

### Post by rlwilson2 on 2008-01-17
> Could you issue this command on the console and post the results:

Code:

lspci



bob@bob-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bob@bob-desktop:~$

---

### Post by rlwilson2 on 2008-01-17
anyone have ideas...  would I have the same problems with pclinuxos?

---

### Post by Sef on 2008-01-17
> Ran Memory Check on the Ubuntu disk no failures What next???

You should run the memory check (mem86 test) at least 8 hours.   One or two passes might not pick up a problem.

---

### Post by Mithrilhall on 2008-01-18
> 
Try adding "acpi=off irqpoll" to the kernel boot options (in /boot/grub/menu.lst). This solved a similar problem I had.


Did you try this yet?

---

### Post by rlwilson2 on 2008-01-18
> Did you try this yet? 

Not exactly sure how to do it???

---

### Post by rlwilson2 on 2008-01-19
Ran memory check over night  no problems there...  

I do not know how to modify the kernel I can get to the file I just do not know where or how to put in the command.  

This freezing problem looks to be common so I assume that there is a fix....  I have a ATI radeon express 200 built in video could this be the issue??  I ran PCLinuxOS and had no freezing problems but had wireless net problems and I like the Ubuntu system better I just have to get over this issue....  Thanks.

---

### Post by birddawg on 2008-01-19
I'm having a similiar problem.  I get random freezes with and without a browser running.  Also, other windows will cause a freeze.  Crtl-alt-backspace does not respond.  
Sometimes, screen goes black and the login screen appears and  I have to log in again.

I found this in my daemon.log file

"gdm[5371] WARNING: gdm_slave_xioerror_handler: Fatal x error - Restarting :0"

Best I can tell, this happened when the desktop would disappear and the login screen would pop up.  

What I'm wondering here is maybe these two issues are related.

Are you having similiar problems?

You mentioned in an earlier post your video card.  Do you think it is video related?

---

### Post by danyf on 2008-01-23
> **rlwilson2 said:**
> Not exactly sure how to do it???

Run the following lines in a terminal:
# --------------------------
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo sed -e 's/vmlinuz\(.*\)$/vmlinuz\1 acpi=off irqpoll/' /boot/grub/menu.lst > /tmp/menu.lst
sudo mv /tmp/menu.lst /boot/grub/menu.lst
# --------------------------
and reboot.

---

### Post by richuu on 2008-01-23
There's a load of pages on this already, on this thread:

[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

Might be something there to help you.

---

### Post by rlwilson2 on 2008-01-24
> Run the following lines in a terminal:
# --------------------------
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo sed -e 's/vmlinuz\(.*\)$/vmlinuz\1 acpi=off irqpoll/' /boot/grub/menu.lst > /tmp/menu.lst
sudo mv /tmp/menu.lst /boot/grub/menu.lst
# --------------------------
and reboot.

I did this no change (thanks for the code though)  I started writing times when if freezes and noticed and XX:16 it always freezes!  Would the log reveal anything?  if so which log...    I need this to work I work from home on the CPU...  I Love the system except for this bug...  Lets Squash it!!!

---

### Post by rlwilson2 on 2008-01-25
Bump

---

### Post by gearshifter on 2008-01-25
I have the same problem here.  Just seems to happen with the firefox browser only.  Not outside of it...

---

### Post by rlwilson2 on 2008-01-28
Switched to Kubuntu 7.10 with Oprea browser... 2 day now no problems....   Why is that???

---

### Post by davit on 2008-01-28
> **gearshifter said:**
> I have the same problem here.  Just seems to happen with the firefox browser only.  Not outside of it...

I am having a similar problem with & during Firefox browsing with multiple tabs, and sometimes  after closing Firefox altogether.  

I noticed that Firefox is not ideal for multi tabs use in Windows aswell. its eats CPU.  My guess is there is a link.  The trouble has some symptoms, like auto hoping from one click hotspot or tab to another, and gradually overloads CPU with commands,  like clicking too many times and not getting a response,  but these click/commands are queued in CPU time, hence CPU overload and eventually freeze like response. However, I like confirm this.

Pent 4 Gutzy on a 1.8Ghz 500Ram

---

### Post by Eycks on 2008-02-02
My Ubuntu 7.10 screen becomes a series of vertical lines and the only way I can recover is to reboot. As suggested here is the output of lspci:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

