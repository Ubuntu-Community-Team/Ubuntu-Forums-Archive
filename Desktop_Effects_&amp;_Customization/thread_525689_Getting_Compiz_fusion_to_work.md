---
title: "Getting Compiz fusion to work"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by shorty28898 on 2007-08-14
I did what the websites tell me to do.  and i go to system and see that compiz fusion manager, but dont know how to get the effects to work.  Also the desktops effects dont seem to work that well.  when i go to desktop effects, it freezes ubuntu, and when it does work, i cant get the work station cube thing to work. but can someone help me getting the effects of compiz fusion to work?

---

### Post by tgm4883 on 2007-08-14
what are you system specs?  What is the output of
glxinfo | grep direct

---

### Post by shorty28898 on 2007-08-14
I dont know what your second quesiton is asking.  but these are my specs.
3 ghz pentium 4 HT
1 gb RAM
130 gb hard drive
windows XP/ubuntu
 what else do you need?

---

### Post by tgm4883 on 2007-08-14
what kind of video card?

as for my second question, open up a terminal, type this
glxinfo | grep direct

copy and paste the result of that command in a reply here.

---

### Post by shorty28898 on 2007-08-14
i dont know my video card, and when i cop and paste that to terminal it comes back with:
direct rendering: yes

---

### Post by tgm4883 on 2007-08-14
can you post the output of lspci

---

### Post by shorty28898 on 2007-08-14
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)

---

### Post by shorty28898 on 2007-08-15
so..?

---

### Post by petit.padavoine on 2007-08-15
What do you mean by "I did what the websites tell me?"
That's kinda vague, there are several different ways to install compiz fusion.
Your card is an intel integrated card (that's what lspci says) but it supports 3D accelaration ("direct rendering:Yes"). It should (technically) support compiz fusion.
If I were you I'd uninstall compiz fusion and try compiz without the fusion plugins (via Deskto Effects)

---

### Post by shorty28898 on 2007-08-15
i re installed ubuntu to start fresh, and now when i do the desktop effects, the top bar on every window is not there, and it docks to the top of the screen.  and i do like all the sudo get stuff, and then after finishing the last step, i dont know how to play around with it.

---

### Post by tgm4883 on 2007-08-15
did you follow a guide of some sort? Which one?

---

### Post by petit.padavoine on 2007-08-15
> **shorty28898 said:**
> i re installed ubuntu to start fresh, and now when i do the desktop effects, the top bar on every window is not there, and it docks to the top of the screen.  and i do like all the sudo get stuff, and then after finishing the last step, i dont know how to play around with it.

Maybe your system just doesn't support the effects, although I doubt it 'cos you do have 3D acceleration...

I dunno, I'm stumped.

EDIT: here's what the compiz site has to say about intel video cards: [http://compiz.org/Intel](http://compiz.org/Intel) (basically use the xf86-video-i810 driver, so ```
sudo apt-get install xf86-video-i810
```

---

### Post by shorty28898 on 2007-08-16
Ok now i have installed ubuntu 3 times.  I dont know it just seems like me and ubuntu do not get along.  Now it says that HAL failed to initiiaze, and since it has said that (when i updated HAL i tihnik is when it started) it can not detect my internet

uninstalled then reinstalled (using WUBI), and updated, then tried what u said and this showed:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xf86-video-i810


um, help?

---

### Post by Salpiche on 2007-08-23
I am having the same issue, yet I have not been able to use any of the effects to work.
BTW I am using Kubuntu

here is my video card info

pichin@Taino:~$ glxinfo | grep direct && lspci
direct rendering: Yes
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:0d.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

---

### Post by shortybookit on 2007-09-03
i am having the same problem all these guys have been having so i started this topic back up


help plz

---

